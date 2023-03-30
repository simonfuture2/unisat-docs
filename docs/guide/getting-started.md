# Getting Started

To develop for Unilite Wallet, install Unilite Wallet on your development machine. [Download here](https://unisat.io/) [New domain URL TBD] 

::: warning A quick note...
This guide assumes intermediate knowledge of HTML, CSS, and JavaScript.
:::

Once Unilite Wallet is installed and running, you should find that new browser tabs have a `window.unilite` object available in the developer console.
This is how your website will interact with Unilite Wallet.

[comment]: <> (## Basic Considerations)

### Browser Detection

To verify if the browser is running Unilite Wallet, copy and paste the code snippet below in the developer console of your web browser:

```javascript
if (typeof window.unilite !== 'undefined') {
  console.log('Unilite Wallet is installed!');
}
```

You can review the full API for the `window.unilite` object [here](./unisat-provider.html).

### Connecting to Unisat Wallet

"Connecting" or "logging in" to Unilite Wallet effectively means "to access the user's Litecoin account(s)".

You should **only** initiate a connection request in response to direct user action, such as clicking a button.
You should **always** disable the "connect" button while the connection request is pending.
You should **never** initiate a connection request on page load.

We recommend that you provide a button to allow the user to connect Unilite Wallet to your dapp.
Clicking this button should call the following method:

```javascript
unilite.requestAccounts()
```

### Demo 

- [Online Demo](https://demo.unisat.io)
- [Demo source code](https://github.com/unisat-wallet/unisat-web3-demo) 

