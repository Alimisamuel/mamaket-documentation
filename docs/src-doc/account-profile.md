---
sidebar_position: 1
---

# Account Profile

This folder contains three folder `components` , `layouts` and `pages` for the user profile section 

In this folder you'll find everything
- Profile
- Mamapurse
- My Orders
- Address
- Security
- Notification
- Help Center

```json
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

```

## Components

## Address

`/components/Address/` this directory contains everything about the user address, `add`, `view` and `edit` address

### Address/AddAddress
The `AddAddress` component is a React functional component that provides a form for users to add a new address. It includes functionality to fetch and select countries, states, and cities, and allows the user to save the address.

#### Functionality

#### State Management
The component uses React's useState hook to manage various pieces of state:

- **open**: Boolean to control the modal's visibility.
- **selectedCountry, selectedState, selectedCity**: Strings to store the selected country, state, and city.
- **countryID, stateID, cityID**: IDs of the selected country, state, and city.
- **zip**: String to store the ZIP code.
- **address**: String to store the address.
- **checked**: Boolean to control the default address checkbox.

#### GraphQL Queries and Mutations
- **GET_COUNTRIES, GET_STATES, GET_CITY**: GraphQL queries to fetch the list of countries, states, and cities.
- **ADD_ADDRESS**: GraphQL mutation to add a new address.

#### useLazyQuery
`useLazyQuery` is used to execute GraphQL queries lazily.

```jsx title=""
const [getCountries, { loading, error, data }] = useLazyQuery(GET_COUNTRIES);
const [getState, { loading: stateLoad, error: statError, data: stateData }] = useLazyQuery(GET_STATES);
const [getCity, { loading: cityLoad, error: cityError, data: cityData }] = useLazyQuery(GET_CITY);
```
#### useMutation
`useMutation` is used to execute the GraphQL mutation for adding a new address.

```jsx title=""
const [addAddress, { loading: addLoading, data: addData }] = useMutation(ADD_ADDRESS);
```
The component renders:

A button to open the modal.
A modal containing the form inputs for address, country, state, and city selection.
Loading indicators while data is being fetched or the mutation is being executed.


### EditAddress
The `EditAddress` component is a React functional component that provides a form for users to edit an existing address. It includes functionality to fetch and select countries, states, and cities, and allows the user to update the address.

#### State Management
The component uses React's useState hook to manage various pieces of state:

- **open**: Boolean to control the modal's visibility.
- **selectedCountry, selectedState, selectedCity**: Strings to store the selected country, state, and city.
- **countryID, stateID, cityID**: IDs of the selected country, state, and city.
- **zip**: String to store the ZIP code.
- **address**: String to store the address.
- **checked**: Boolean to control the default address checkbox.

#### GraphQL Queries and Mutations

- **GET_COUNTRIES, GET_STATES, GET_CITY**: GraphQL queries to fetch the list of countries, states, and cities.
- **EDIT_ADDRESS**: GraphQL mutation to edit an existing address.

#### useEffect for Selected Address
The `useEffect` hook updates the state with the selected address details when the selectedAddress prop changes.

 ```jsx
useEffect(() => {
    setAddress(selectedAddress?.addressOne);
    setCityID(selectedAddress.city?._id);
    setSelectedCity(selectedAddress.city?.name);
    setZip(selectedAddress?.zipCode);
    setCountryID(selectedAddress?.country?._id);
    setSelectedCountry(selectedAddress?.country?.name);
    setSelectedState(selectedAddress?.state?.name);
    setStateID(selectedAddress?.state?._id);
    setChecked(selectedAddress?.isDefault);
}, [selectedAddress]);
```

## Mamapurse

### AddCash Component
The `AddCash` component in React enables users to add funds to their account using the Stripe API. It handles the display and functionality of a modal that facilitates this process. Below is a detailed explanation of the functions and the overall functionality of the component.

#### Stripe Initialization
The component initializes Stripe with the public key from environment variables.

``` jsx
const p_Key = process.env.REACT_APP_STRIPE_KEY;
const stripePromise = loadStripe(p_Key);
```

#### Amount Change Handler
This handler updates the state when the amount input changes, ensuring the value is a valid number.
``` jsx
const handleAmountChange = (e) => {
  const newValue = parseFloat(e.target.value);
  if (!isNaN(newValue)) {
    setAmount(newValue);
  } else {
    setAmount(null);
  }
};
```
#### useMutation for Initializing Wallet Funding
This mutation initializes the wallet funding process with the entered amount. On completion, it stores the client secret and sets the state to indicate initialization.

```jsx 
const [initializeWallet, { data, loading }] = useMutation(ADD_FUNDS, {
  onCompleted: (queryData) => {
    let data = queryData.initializeWalletFunding;
    setClientSecret(data.client_secret);
    localStorage.setItem("amount", amount);
    setIsInitialized(true);
  },
});
```

#### Handler for Initializing Wallet
This handler resets the initialized state and triggers the mutation to initialize wallet funding.

```jsx 
const handleInitializeWallet = () => {
  setIsInitialized(false);
  initializeWallet({
    variables: {
      amount,
    },
  });
};
```

### Card Input
The `CardInput` component is a React functional component that integrates with the Stripe API to handle payment processing. It uses the Stripe.js and React Stripe.js libraries to create and manage the payment form.

#### State Management
The component uses React's `useState` hook to manage various pieces of state:

- **message**: String to store messages related to the payment status.
- **isLoading**: Boolean to control the loading state of the form submission.

#### Stripe Elements
- **useStripe**: A hook provided by Stripe.js to access the Stripe instance.
- **useElements**: A hook provided by Stripe.js to access the Elements instance, which is used to create the payment form.

#### useEffect Hook
The useEffect hook is used to check the payment status after the component mounts. It retrieves the client secret from the URL and calls stripe.retrievePaymentIntent to get the status of the payment intent.
``` jsx
useEffect(() => {
    if (!stripe) {
        return;
    }

    const clientSecret = new URLSearchParams(window.location.search).get("payment_intent_client_secret");

    if (!clientSecret) {
        return;
    }

    stripe.retrievePaymentIntent(clientSecret).then(({ paymentIntent }) => {
        switch (paymentIntent.status) {
            case "succeeded":
                alert("we did it");
                setMessage("Payment succeeded!");
                break;
            case "processing":
                setMessage("Your payment is processing.");
                break;
            case "requires_payment_method":
                handleAlert(`Your payment was not successful, please try again.`, "error");
                setMessage("Your payment was not successful, please try again.");
                break;
            default:
                setMessage("Something went wrong.");
                break;
        }
    });
}, [stripe]);
```

#### Rendering
The component renders:

- A loading indicator if Stripe.js hasn't yet loaded.
- A PaymentElement for the payment form.
- A button to submit the payment form, which is disabled when loading or when Stripe.js hasn't loaded.
- Messages to display the status of the payment.

The payment form uses the PaymentElement component provided by Stripe.js to handle the payment details.
```jsx 
return (
    <form id="payment-form" onSubmit={handleSubmit}>
        {!stripe && !elements && (
            <Box align="center">
                <img
                    src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Loading_icon.gif"
                    width={150}
                />
            </Box>
        )}
        {elements && (
            <PaymentElement id="payment-element" options={{ layout: "tabs" }} />
        )}

        <Box sx={{ mt: 3 }}>
            <Button
                disabled={isLoading || !stripe || !elements}
                onClick={handleSubmit}
                variant="contained"
                fullWidth
            >{`Pay Now $${amount}`}</Button>
        </Box>

        {/* Show any error or success messages */}
        {message && <Typography id="payment-message">{message}</Typography>}
    </form>
);
```

## Security
### ChangePassword
The `ChangePassword` component is a React functional component that provides a form for users to change their password. It includes validation, password visibility toggle, and integrates with GraphQL to update the password on the server.

#### State Management
The component uses React's useState hook to manage various pieces of state:

- **open**: Boolean to control the modal's visibility.
- **success**: Boolean to control the visibility of the success alert.
- **showPassword**: Boolean to toggle password visibility.
- **currentPassword**: String to store the current password.

#### GraphQL Mutation
CHANGE_PASSWORD: GraphQL mutation to change the user's password
```jsx
const [changePassword, { loading, error, data }] = useMutation(CHANGE_PASSWORD);
```

#### Formik
The component uses Formik to manage form state and validation:
```jsx
const { values, errors, handleBlur, handleChange, handleSubmit } = useFormik({
  initialValues: {
    password: "",
    confirmPassword: "",
  },
  validationSchema: validationSchema,
  onSubmit: (values) => {
    setSuccess(false);
    changePassword({
      variables: {
        currentPassword: currentPassword,
        newPassword: values.password,
      },
    })
 ...
  },
});
```

#### Validation Schema
The validation schema uses Yup to enforce password rules:
```jsx 
const validationSchema = Yup.object().shape({
  password: Yup.string()
    .min(8, "Password must be at least 8 characters")
    .required("Password is required"),
  confirmPassword: Yup.string()
    .oneOf([Yup.ref("password"), null], "Passwords must match")
    .required("Confirm Password is required"),
});
```

### Change Pin
The `ChangePin` component is a React functional component that provides a modal form for users to change their transaction PIN. It includes input validation, mutation handling, and feedback notifications.

## Layout
### My Account
The `MyAccount` component is a React functional component that renders a user's account page. This page includes navigation links to different account-related sections, a logout button, and common layout components like a navbar, newsletter section, and footer.

:::danger Mobile Component

This component is for smaller device screen or mobile screens only

:::

#### handleLogOut
```jsx
const handleLogOut = () => {
    navigate("/");
    dispatch(logoutUser());
};
```
#### Navigation Links
```jsx
<Box sx={...}>
  {NavData.map((nav, index) => (
    <Link to={nav.link} key={index}>
      <Box sx={...}>
        <Typography sx={...}>{nav.title}</Typography>
        <ChevronRightIcon sx={{ color: "#333" }} />
      </Box>
    </Link>
  ))}
</Box>
```

### Shared Layout
The `SharedLayouts` component is a layout component for a React application. It serves as a container for other components and includes common elements such as navigation bars, side navigation, breadcrumbs, newsletter subscription, and footer for user profile outlet.

### SideNav
The SideNav component is a React functional component that renders a side navigation bar. It uses data from NavData to create navigation links and highlights the currently selected link based on the current URL path. The side navbar on `Profile` screen.

## Pages



