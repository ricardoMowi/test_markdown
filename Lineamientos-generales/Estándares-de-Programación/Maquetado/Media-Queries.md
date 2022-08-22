Actualmente el lineamiento es el desarrollo con styled components.

Para trabajarlos usamos el siguiente helper disponibilizado en la prima ui elements https://dev.azure.com/PrimaAFPTeam/PrimaFrontend/_git/prima-ui-elements?path=%2Fsrc%2Flib%2Futils%2Fmedia%2FstyledConfig.js

![image.png](/.attachments/image-d7fb4c04-e909-4ea1-ac30-c82fdd5c20c5.png)

```js
import styled from 'styled-components';
import { media } from "@prima/prima-ui-elements/dist/utils/media/styledConfig";

...

const WrapperStyled = styled.div`
  background: red;
  ${
    media.md`
      background: blue;
    `
  }
`;


```