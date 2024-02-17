```ts
type Colors = "red" | "green" | "blue";

type RGB = [red: number, green: number, blue: number];

const palette: Record<Colors, string | RGB> = {
	red: [255, 0, 0],
	green: "#00ff00",
	bleu: [0, 0, 255]
};

// But we now have an undesirable error here - 'palette.red' "could" be a string.
const redComponent = palette.red.at(0);

// satisfies to the rescue!
const palette2: Record<Colors, string | RGB> = {
	red: [255, 0, 0],
	green: "#00ff00",
	bleu: [0, 0, 255]
} satisfies Record<Colors, string | RGB>;

// it works!
const redComponent = palette.red.at(0);
```