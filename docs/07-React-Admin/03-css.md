
在组件中增加css：

```
import * as React from "react";
import { Header } from "./header";

export class Home extends React.Component<{}, {}> {
    render() {
        const css = `
        .landing-page {
            background-color: orange;
        }
        `
        return (
            <div>
                <style>
                    {css}
                </style>
                <div id="page-top" className="landing-page">
                    <Header />
                </div>
            </div>  
        );
    }
}
```

