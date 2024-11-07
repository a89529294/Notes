```js
import { cache } from "react";

const ProductCache = cache((): {productDetails?: ProductDetails} => ({productDetails: undefined}));

export const getProductDetails = async (productID?: string) => {
  if (productID) {
    const productDetails = await executeSql("SELECT * from products where id=?", productID);
    ProductCache().productDetails = productDetails;
    return productDetails;
  }
  const productDetails = ProductCache().productDetails;
  if (productDetails === undefined) {
    throw new Error("Can't get product details unless it has been hydrated first!")
  }
  return productDetails;
}
```

```js
// file: /app/products/[productID]/page.tsx
import ProductDetails from "./ProductDetails";
import getProductDetails from "./getProductDetails";

type PageParams = {
  params: {
    productID: string;
  }
}

export default function Page(props: PageParams) {
  const { productTitle } = await getProductDetails(props.params.productID);

  return <div>
    <h1>{productTitle}</h1>
    <ProductDetails />
}

// file /app/products/[productID]/ProductDetails.tsx
import ProductImages from "./ProductImages";

export default function ProductDetails() {
  const { description, price } = await getProductDetails();

  return <div>
    <ProductImages />
    <div>
       <p>{description}</p>
       <button onPress={() => addToCart(props.productID)}>{price}</button>
    </div>
  </div>
}

// file /app/products/[productID]/ProductImages.tsx

export default function ProductImages(props: { productID: string}) {
  const { images } = await getProductDetails();

  return <div>
    {images.map(src => <img src={src} />}
  </div>
}
```