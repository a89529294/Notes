```tsx
import dynamic from "next/dynamic";

const ClientOnlyHeader = dynamic(()=>import('path/to/Header'), {ssr:false})
```