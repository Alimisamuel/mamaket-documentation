---
sidebar_position: 4
---

# Plugins

### Mamaket Plugins Configuration

This section provides the configuration details for Mamaket plugins. Below is the `package.json` configuration for the Mamaket admin application.

```json
{
  "name": "mamaket",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "@apollo/client": "^3.8.0",
    "@emotion/react": "^11.10.8",
    "@emotion/styled": "^11.10.8",
    "@greatsumini/react-facebook-login": "^3.3.3",
    "@mui/icons-material": "^5.11.16",
    "@mui/lab": "^5.0.0-alpha.129",
    "@mui/material": "^5.12.3",
    "@mui/styles": "^5.15.12",
    "@react-oauth/google": "^0.11.1",
    "@reduxjs/toolkit": "^1.9.5",
    "@stripe/react-stripe-js": "^2.1.2",
    "@stripe/stripe-js": "^2.1.1",
    "@testing-library/jest-dom": "^5.14.1",
    "@testing-library/react": "^13.0.0",
    "@testing-library/user-event": "^13.2.1",
    "aos": "^2.3.4",
    "apollo-upload-client": "^18.0.1",
    "autosuggest-highlight": "^3.3.4",
    "date-fns": "^2.30.0",
    "dotenv": "^16.3.1",
    "firebase": "^10.12.2",
    "formik": "^2.4.3",
    "framer-motion": "^11.0.6",
    "graphql": "^16.7.1",
    "isomorphic-fetch": "^3.0.0",
    "mailchimp-api-v3": "^1.15.0",
    "moment": "^2.29.4",
    "mui-one-time-password-input": "^2.0.2",
    "mui-tel-input": "^4.0.0",
    "notistack": "^3.0.1",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-facebook-login": "^4.1.1",
    "react-google-login": "^5.2.2",
    "react-icons": "^4.12.0",
    "react-lottie": "^1.2.4",
    "react-mailchimp-subscribe": "^2.1.3",
    "react-redux": "^8.1.2",
    "react-router-dom": "^6.11.1",
    "react-router-hash-link": "^2.4.3",
    "react-scripts": "5.0.0",
    "react-scroll": "^1.8.9",
    "react-slick": "^0.29.0",
    "react-toastify": "^10.0.5",
    "redux-persist": "^6.0.0",
    "slick-carousel": "^1.8.1",
    "socket.io-client": "^4.7.2",
    "uuid": "^9.0.1",
    "web-vitals": "^2.1.0",
    "yup": "^1.2.0"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ]
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  },
  "devDependencies": {
    "cross-env": "^7.0.3"
  }
}

```

- **@apollo/client**: A comprehensive state management library for JavaScript that enables you to manage both local and remote data with GraphQL.
- **@emotion/react**: A library designed for writing CSS styles with JavaScript.
- **@emotion/styled**: Allows you to style React components using a styled-components-like syntax.
- **@greatsumini/react-facebook-login**: A component for integrating Facebook login into your React application.
- **@mui/icons-material**: Material Design icons for use with Material-UI.
- **@mui/lab**: The incubator for Material-UI components that are not yet ready to be included in the main package.
- **@mui/material**: Material-UI library that provides React components that implement Google's Material Design.
- **@mui/styles**: The legacy styling solution for Material-UI, useful for writing CSS-in-JS.
- **@react-oauth/google**: A library for integrating Google OAuth into your React application.
- **@reduxjs/toolkit**: The official, recommended way to write Redux logic.
- **@stripe/react-stripe-js**: React components for Stripe.js and Elements.
- **@stripe/stripe-js**: The official Stripe.js library wrapper.
- **@testing-library/jest-dom**: Custom jest matchers to test the state of the DOM.
- **@testing-library/react**: Simple and complete React DOM testing utilities that encourage good testing practices.
- **@testing-library/user-event**: Library to simulate user interactions.
- **aos**: Animate on scroll library for adding animations to your site as you scroll.
- **apollo-upload-client**: Apollo client extension for file uploads via GraphQL mutations.
- **autosuggest-highlight**: Utility for highlighting matched parts of text in autosuggest components.
- **date-fns**: Modern JavaScript date utility library.
- **dotenv**: Loads environment variables from a .env file into process.env.
- **firebase**: Firebase library for integrating Firebase services into your application.
- **formik**: Formik makes forms in React easy by managing form state and validation.
- **framer-motion**: A library to create animations in React.
- **graphql**: A query language for your API, and a runtime for executing those queries.
- **isomorphic-fetch**: A universal fetch API for Node.js and the browser.
- **mailchimp-api-v3**: Node.js wrapper for the MailChimp API v3.
- **moment**: A library for parsing, validating, manipulating, and formatting dates.
- **mui-one-time-password-input**: A Material-UI component for OTP input.
- **mui-tel-input**: A Material-UI component for telephone input.
- **notistack**: A notification library which makes it easy to display notifications.
- **react**: A JavaScript library for building user interfaces.
- **react-dom**: React package for working with the DOM.
- **react-facebook-login**: A component for integrating Facebook login into your React application.
- **react-google-login**: A component for integrating Google login into your React application.
- **react-icons**: Include popular icons in your React projects easily.
- **react-lottie**: A React wrapper for lottie-web.
- **react-mailchimp-subscribe**: A simple Mailchimp form in React that integrates with Mailchimp’s embedded forms.
- **react-redux**: Official React bindings for Redux.
- **react-router-dom**: Declarative routing for React web applications.
- **react-router-hash-link**: A React component to scroll to elements within a page using hashes in the URL.
- **react-scripts**: The scripts and configuration used by Create React App.
- **react-scroll**: React component for animating vertical scrolling.
- **react-slick**: Carousel component built with React.
- **react-toastify**: Allows you to add notifications to your app with ease.
- **redux-persist**: Persist and rehydrate a Redux store.
- **slick-carousel**: Carousel library.
- **socket.io-client**: Realtime application framework.
- **uuid**: Library for generating UUIDs.
- **web-vitals**: Library for measuring web performance.
- **yup**: JavaScript schema builder for value parsing and validation.

