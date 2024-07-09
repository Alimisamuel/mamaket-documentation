---
sidebar_position: 3
---

# Styling 

 The website is built using **Mui - Material UI**

 ## Material-UI Styling Documentation
 This documentation provides guidelines on using Material-UI (MUI) for styling in your React website. Material-UI is a popular React UI framework that provides pre-built components and styling solutions based on Google's Material Design principles.



Conclusion
This documentation provides an overview of using Material-UI to style the Mamaket website. For detailed component usage and further customization, refer to the official Material-UI documentation at [Material-UI Documentation](https://mui.com/material-ui/getting-started/). Happy coding with Mamaket!

## Theme

The theme configuration file can be found at `/src/styles/theme.js`. This file contains the custom theme settings for your Material-UI components.

``` jsx
import { createTheme } from "@mui/material";

const Theme = createTheme({
  palette: {
    primary: {
      // main: "#2E1834",
      main: "#2E1834",
    },
  },
  components: {
    MuiButton: {
      styleOverrides: {
        contained:{
          backgroundColor:'#5C3069'
        }
      },
    },
  },
  typography: {
    h1: {
      fontFamily: "syne",
      fontWeight: 700,
      fontSize: "110px",
      color: "#fff",
      lineHeight: { lg: "98px", xs: "50px" },
    },
    h2: {
      fontFamily: "inter",
      fontWeight: 300,
      color: "#fff",
      fontSize: "20px",
      lineHeight: "30px",
    },
    button: {
      fontFamily: "inter",
      textTransform: "initial",
    },
    caption: {
      fontFamily: "inter",
      fontWeight: 400,
      fontSize: "12px",
      color: "#1a1a1a",
    },
    subtitle1: {

  },
....
```

## Global css

This file can be found at `/src/styles/main.css`. This file contains the global css styling, font urls, font settings.


