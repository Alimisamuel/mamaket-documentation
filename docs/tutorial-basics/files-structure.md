---
sidebar_position: 2
---

# File  Structure

## Overview
The following is the file structure for the Mamaket web application:

```json
  mamaket_web/
├── public/
│   ├── index.html
│   ├── favicon.ico
│   ├── site.webmanifest.json
│   ├── robot.txt
│   └── manifest.json
├── src/
│   ├── Account-Profile/
│   │   ├── components/
│   │   └── layout/
│   ├── assets/
│   │   ├── anime/
│   │   ├── banner/
│   │   ├── Carousel/
│   │   ├── Data/
│   │   ├── Flags/
│   │   ├── Icons/
│   │   ├── Logo/
│   │   ├── Offer/
│   │   └── Products/
│   ├── Chat/
│   │   ├── Chat.js
│   │   ├── ChatList.js
│   │   ├── ChatMobile.js
│   │   └── ChatOutlet.js
│   ├── components/ 
│   │   ├── Alert
│   │   ├── Blog
│   │   ├── Cards
│   │   ├── Cart
│   │   ├──Categories
│   │   ├── Checkout
│   │   ├──Common
│   │   ├── Products
│   │   ├──Search
│   │   └── Services
│   ├── FooterContent/
│   │   ├── Blog
│   │   ├── About.js
│   │   ├── Ads.js
│   │   ├── Contact.js
│   │   ├── Faq.js
│   │   ├── Index.js
│   │   ├── Mamapurse.js
│   │   ├── Payment.js
│   │   ├── PrivacyPolicy.js
│   │   ├── ProductDoc.js
│   │   ├── ReturnPolicy.js
│   │   ├── TermsCondition.js
│   │   └── Verification.js
│   ├── Hooks/
│   │   ├── useAddToCart.js
│   │   ├── useAddToFav.js
│   │   ├── useDecrease.js
│   │   ├── useGetCart.js
│   │   ├── useGetFav.js
│   │   ├── useGetService.js
│   │   ├── useIncrease.js
│   │   ├── useRemoveCarts.js
│   │   └── useRemoveFav.js
│   ├── pages/
│   │   ├── Auth
│   │   └──Screens
│   ├── store/
│   │   ├── favouriteSlice.js
│   │   ├── productSlice.js
│   │   ├── serviceSlice.js
│   │   ├── store.js
│   │   └── userSlice.js
│   ├── styles/
│   │   ├── Main.css
│   │   └──Theme.js
│   ├── utils/
│   │   ├── ApolloInstance.js
│   │   ├── Cache.js
│   │   ├── firebaseConfig.js
│   │   ├── index.js
│   │   ├── Mutation.js
│   │   ├── ProtectedRoute.js
│   │   ├── Queries.js
│   │   ├── Schema.js
│   │   ├── socket.js
│   │   └── StatusCode.js
│   ├── App.js
│   ├── index.css
│   ├── index.js
│   ├── Routes.js
│   └── ScrollToTop.js
├── .env
├── .gitignore
├── package.json
├── README.md
└── yarn.lock

```

### Project Root

- `mamaket_web/`: Root directory of the React project.
  - `.gitignore`: Specifies files and directories to be ignored by Git.
  - `package.json`: Contains project metadata and dependencies.
  - `README.md`: Project documentation.
  - `yarn.lock`: Lock file for Yarn package manager to ensure consistent installs.
### Public Directory

- `public/`: Root directory of the React project.
  - `.index.html`: The main HTML file that includes a div with id `root` and also contains script links, meta data, project title and description .
  - `favicon.ico`: The favicon for the application.
  - `manifest.json`:Metadata for Progressive Web App (PWA)
  - and other relative files

### Src Directory
- `src/`: Contains the source code of the application.

This section has been exported to a new page for a better experience and arrangement. [Go to Src Directory](/docs/category/src---doc):

 <!-- ### Account Profile -->

<!-- ```json
Account-Profile/
├── Components/
│   ├── Address/
│   │   ├──AddAddress.jsx
│   │   ├──EditAddress.jsx
│   ├── Mamapurse/
│   │   ├──AddCash.jsx
│   │   ├──CardInput.jsx
│   │   ├──Cashout.jsx
│   │   ├──Confirmation.jsx
│   └── Security/
│   │   ├──ChangePassword.jsx
│   │   ├──ChangePin.jsx
├── Layouts/
│   ├── MyAccount.js
│   ├── SharedLayouts.js
│   ├── SideNav.js

``` -->


### Configuration Files
- `.gitignore`: Specifies files and directories to be ignored by Git.
- `package.json`: Contains project metadata and dependencies.
- `README.md`: Project documentation.
- `yarn.lock`: Lock file for Yarn package manager to ensure consistent installs.
### Environment Files
- `.env`: Default environment variables for the application.
- `.env.development`: Environment variables specific to the development environment.
- `.env.production`: Environment variables specific to the production environment.

```json title="env key names"
***_**_STRIPE_KEY : This key is used for implementing Stripe API payment in Mamapurse.

**_**_GRAPHQL_URL : This environment key, `***_**_GRAPHQL_URL`, specifies the URL endpoint for the GraphQL API used in the React application.

*****_****_SOCKET_URL : key used to specify the WebSocket URL for real-time communication(chat) between the buyer and seller .

********_***_GOOGLE_CLIENT_ID : key used for implementing the Google auth in the signin and signup component


```

This documentation provides a clear layout of the project, helping developers understand the organization and purpose of each directory and file.

