# ICO (Initial Coin Offering)

Now its time for you to launch a token for `Crypto Devs`. Let's call the token Crypto Dev Token.

![](https://i.imgur.com/78uY3Mm.png)

---
## Build

## Requirements

- There should be a max of `10,000 CD` tokens.
- Every `Crypto Dev` NFT holder should get 10 tokens for free but they would have to pay the gas fees.
- The price of one CD at the time of ICO should be `0.001 ether`
- There should be a website which users can visit for the ICO.

Let's start building 🚀

- Project in continuation to [nft_collection](https://github.com/sumitdevtech/nft_collection)

## Theory

- What is an ERC20?
  - ERC-20 is a technical standard; it is used for all smart contracts on the Ethereum blockchain for token implementation and provides a list of rules that all Ethereum-based tokens must follow.
  - Please look at all the ERC20 [functions](https://docs.openzeppelin.com/contracts/2.x/api/token/erc20) before moving ahead

## Build

### Smart Contract

To build the smart contract we would be using [Hardhat](https://hardhat.org/).Hardhat is an Ethereum development environment and framework designed for full stack development in Solidity. In simple words you can write your smart contract, deploy them, run tests, and debug your code.

- To setup a Hardhat project, Open up a terminal and execute these commands

  ```bash
  mkdir hardhat
  cd hardhat
  npm init --yes 
  or 
  yarn init --yes
  npm install --save-dev hardhat 
  or
  yarn add hardhat --dev
  ```
- In the same directory where you installed Hardhat run:

  ```bash
  npx hardhat
  ```

  - Select `Create a basic sample project`
  - Press enter for the already specified `Hardhat Project root`
  - Press enter for the question on if you want to add a `.gitignore`
  - Press enter for `Do you want to install this sample project's dependencies with npm (@nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers)?`

Now you have a hardhat project ready to go!

If you are not on mac, please do this extra step and install these libraries as well :)

```bash
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
or
yarn add @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers --dev
```

- In the same terminal now install `@openzeppelin/contracts` as we would be importing [Openzeppelin's ERC20 Contract](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol) and [Openzeppelin's Ownable Contract](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol) in our `CryptoDevToken` contract

  ```bash
  npm install @openzeppelin/contracts
  or 
  yarn add @openzeppelin/contracts
  ```

- Now, We will call the `CryptoDevs.sol` contract that we had deployed in our previous [repo](https://github.com/sumitdevtech/nft_collection/blob/main/hardhat/contracts/CryptoDevs.sol) to check for owners of CryptoDev NFT's. As we only need to call `tokenOfOwnerByIndex` and `balanceOf` methods, we can create an interface for `CryptoDevs contract` with only these two functions.This way we would save `gas` as we would not need to inherit and deploy the entire `CryptoDevs Contract` but only a part of it.

- Create a new file inside the `contracts` directory and call it `ICryptoDevs.sol` and add code as shown in this repo...

- Create a new file inside the `contracts` directory and call it `CryptoDevToken.sol` and add the lines as shown in this repo...

- Now we would install `dotenv` package to be able to import the env file and use it in our config. Open up a terminal pointing at`hardhat` directory and execute this command

  ```bash
  npm install dotenv
  or 
  yarn add dotenv
  ```

- Now create a `.env` file in the `hardhat` folder and add the following lines, use the instructions in the comments to get your Alchemy API Key URL and RINKEBY Private Key. Make sure that the account from which you get your rinkeby private key is funded with Rinkeby Ether as shown in this repo...

- Lets deploy the contract to `rinkeby` network. Create a new file named `deploy.js` under the `scripts` folder

- Now we would write some code to deploy the contract in `deploy.js` file as shown in the repo...

- You would see that the `deploy.js` file requires a constant. Let's create a `constants` folder under `hardhat` folder.
- Inside the `constants` folder create a new file named `index.js` and add the address of the `CryptoDevs.sol` that we had deployed in the previous [nft_collection](https://github.com/sumitdevtech/nft_collection/blob/main/next-app/constants/index.js) repo...

- Now open the `hardhat.config.js` file, we would add the `rinkeby` network here so that we can deploy our contract to rinkeby. Replace all the lines in the `hardhat.config.js` file with the given lines of code as shown in this repo...
  
- Compile the contract, open up a terminal pointing at`hardhat` directory and execute this command

  ```bash
     npx hardhat compile
  ```
  
- To deploy, open up a terminal pointing at`hardhat` directory and execute this command
  ```bash
    npx hardhat run scripts/deploy.js --network rinkeby
  ```
- Save the CryptoDevToken Contract Address that was printed on your terminal in your notepad, you would need it futher down in the tutorial.

### Website

- To develop the website we would be using [React](https://reactjs.org/) and [Next Js](https://nextjs.org/). React is a javascript framework which is used to make websites and Next Js is built on top of React.
- First, You would need to create a new `next` app. Your folder structure should look something like

  ```
     - ICO
         - hardhat
         - next-app
  ```

- To create this `next-app`, in the terminal point to ICO folder and type

  ```bash
      npx create-next-app@latest
  ```

  and press `enter` for all the questions

- Now to run the app, execute these commands in the terminal

  ```
  cd next-app
  npm run dev
  ```

- Now go to `http://localhost:3000`, your app should be running 🤘

- Now lets install Web3Modal library(https://github.com/Web3Modal/web3modal). Web3Modal is an easy-to-use library to help developers add support for multiple providers in their apps with a simple customizable configuration. By default Web3Modal Library supports injected providers like (Metamask, Dapper, Gnosis Safe, Frame, Web3 Browsers, etc), You can also easily configure the library to support Portis, Fortmatic, Squarelink, Torus, Authereum, D'CENT Wallet and Arkane.
  Open up a terminal pointing at`next-app` directory and execute this command

  ```bash
    npm install web3modal
    or 
    yarn add web3modal
  ```

- In the same terminal also install `ethers.js`

  ```bash
  npm i ethers
  or 
  yarn add ethers
  ```

- In your public folder, download the following image (https://github.com/sumitdevtech/nft_collection/blob/main/next-app/public/cryptodevs/0.svg). Make sure that the name of the downloaded image is `0.svg`

- Now go to styles folder and replace all the contents of `Home.modules.css` file with the code shown in this repo...

- Open your `index.js` file under the `pages` folder and paste the code shown in this repo..., explanation of the code can be found in the comments.

- Now create a new folder under the `next-app` folder and name it `constants`.
- In the constants folder create a file, `index.js` and paste the following code.

  - Add `ABI` of the NFT contract that you deployed in the last repo i.e[nft_collection](https://github.com/sumitdevtech/nft_collection/blob/main/next-app/constants/index.js).
  - Add `contract address` of the NFT contract that you deployed in the last repo i.e[nft_collection](https://github.com/sumitdevtech/nft_collection/blob/main/next-app/constants/index.js).
  - Add `ABI` of the token contract. To get the abi of the Token contract, go to `hardhat/artifacts/contracts/CryptoDevToken.sol` and then from`CryptoDevToken.json` file get the array marked under the `"abi"` key.
  - Add `contract address` of the token contract that you saved to your notepad, early on as shown in this repo...

- Now in your terminal which is pointing to `next-app` folder, execute

  ```bash
  npm run dev
  or
  yarn dev
  ```

Your ICO dapp should now work without errors 🚀

---

## Push to Github

Make sure to push all this [code to Github before proceeding to the next step](https://medium.com/hackernoon/a-gentle-introduction-to-git-and-github-the-eli5-way-43f0aa64f2e4).
---

## Deploying your dApp

We will now deploy your dApp, so that everyone can see your website and you can share it with all of your LearnWeb3 DAO friends.

- Go to https://vercel.com/ and sign in with your GitHub
- Then click on `New Project` button and then select your ICO dApp repo
- When configuring your new project, Vercel will allow you to customize your `Root Directory`
- Click `Edit` next to `Root Directory` and set it to `next-app`
- Select the `Framework Preset` as `Next.js`
  ![](https://i.imgur.com/2oJRKgO.png)

- Click `Deploy`
- Now you can see your deployed website by going to your dashboard, selecting your project, and copying the URL from there!

Check my final website here [ICO](https://ico-sumitdevtech.vercel.app/)

Special thanks to team@LearnWeb3DAO
