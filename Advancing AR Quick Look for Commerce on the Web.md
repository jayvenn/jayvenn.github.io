# Chapter 28<br/>Advancing AR Quick Look for Commerce on the Web

Oh iOS developers, today you're going to advance AR Quick Look on the web. AR Quick Look is a system-wide AR content preview framework, and it's definitely not limited to just your app. Particularly with websites that want to leverage AR content in commerce, your iOS device can leverage some magic.

Here's a quote from Bang & Olufsen's Customer Experience Senior Manager, Jakob Kristoffersen:

> Users who engage with the AR experience in our iOS app or on the website are 4X more likely to seek out our Store Finder to visit B&O store and has aided our sales effort to great extents.

Early adopters of AR in commerce has an advantage in that the company offering the products oozes out innovation juice. In addition, the company allows customers to see products at their place (like home). It's like letting the customers visualize products at their home. Because customers can see it at their home, they are more likely to purchase something that fits.

For AR Quick Look to work with Apple Pay, you'll need a device running iOS 13.3 or later. Apple Pay allows users to make purchases conveniently from their devices. As Amazon touted in the past, fewer steps equal easier purchasing, which equals more sales.

In this chapter, you'll learn about the following AR Quick Look in web topics:

* Creating a website for AR Quick Look.
* Integrating Apply Pay to receive payments.
* Creating custom action to create a more personal experience.
* Using custom banner for branding.

This chapter won't go into the details of web-specific technologies like HTML. Rather, it'll focus on AR Quick Look. Without further ado, it's time to dive in.

## Getting Started

Open a **text editor** like Atom, Sublime Text, or TextMate. Add the following code:

```html
<!DOCTYPE html>
<html>
<head>
  <title>AR Quick Look</title>
</head>
<body>
  <h1>Preview a Model in AR Quick Look</h1>
</body>
</html>
```

Here, you have a simple HTML file with a web header name and a header body. Save the **file** as **ARQuickLook.html**.

![Figure 28.1](assets/28/28.1.png)

Open **ARWeb.html**. Opened in Safari, here's what you'll see:

![Figure 28.2](assets/28/28.2.png)

Great! Next, you'll add the quick look buttons in the website.

## ARQuickLook Buttons

ARQuickLook buttons are standardized buttons with the ARKit logo. You can find this in recent places, such as previewing the Pro Display XDR:

![Figure 28.3](assets/28/28.3.png)
  
Add the following code below the `<h1>` tag:
  
```
<a href="gramophone.usdz" rel="ar">
  <img src="gramophone.png" width=160 height=160>
</a>
```

Inside the hyperlink tag, the most important thing to note here is `rel="ar"`. The relationship tag specifies `gramophone.usdz` as `ar`. After the hyperlink tag, you've added an image which sources from `gramophone.png` with a width and height of 160.

Your HTML file should now look like this:

```
<!DOCTYPE html>
<html>
<head>
  <title>AR Quick Look</title>
</head>
<body>
  <h1>Preview a Model in AR Quick Look</h1>
  <a href="gramophone.usdz" rel="ar">
    <img src="gramophone.png" width=160 height=160>
  </a>
</body>
</html>
```

You can find more of Apple's USDZ models at:

```
https://developer.apple.com/augmented-reality/quick-look/
```

Open the **HTML** file in a web browser. And, you should be able to see the following:

![Figure 28.4](assets/28/28.4.png)

Next, you'll learn how to deploy your website with GitHub Pages.

## Deploying Website with GitHub Pages

GitHub Pages are websites for showcasing your projects. Typically, GitHub Pages consist of an accumulation of your GitHub work. As a matter of fact, you can leverage GitHub Pages to display your augmented reality artistry.

Wow, I'm excited. To begin, open **www.github.com**. Create a GitHub profile if you've yet to create one. In the top-right corner, click the **+** button. Then, click the **New repository** button.

![Figure 28.5](assets/28/28.5.png)

Now, name your GitHub repository with the following convention:

```
username.github.io
```

It will look like this:

![Figure 28.6](assets/28/28.6.png)

Scroll down to the bottom of the page, create **Create repository**.

![Figure 28.7](assets/28/28.7.png)

Afterward, look to the top-right corner. Click on your **profile**. Then, select **Settings** from the dropdown menu:

![Figure 28.8](assets/28/28.8.png)

Here's the Settings page:

![Figure 28.9](assets/28/28.9.png)

Scroll down to the GitHub Pages section:

![Figure 28.10](assets/28/28.10.png)

Click **Select theme** to choose your theme.

![Figure 28.11](assets/28/28.11.png)

Replace the markdown file with the following:

```
## AR Showcase

[QuickLook](ARQuickLook.html)
```

So, it'll look like this:

![Figure 28.12](assets/28/28.12.png)

Now, scroll down and **commit** the changes:

![Figure 28.13](assets/28/28.13.png)

Next, you'll upload the website and its resources you created locally onto your website.

## Uploading Resources to GitHub Pages

Click **Code** to open the repository's main page.

![Figure 28.14](assets/28/28.14.png)

Next, click **Add file** dropdown menu. Click **Upload files**.

![Figure 28.15](assets/28/28.15.png)

Select the USDZ, thumbnail, and HTML **files**:

![Figure 28.16](assets/28/28.16.png)

Once the files have completed uploaded, click **Commit changes**.

![Figure 28.17](assets/28/28.17.png)

GitHub will process your newly added files. Now, on your iOS or iPadOS device with an A12 chip or later, open your deployed website. Click **QuickLook** to see the framework in action from the next page.

![Figure 28.18](assets/28/28.18.png)

On the QuickLook page, you'll see that a gramophone image with an ARKit badge thanks to the AR relationship tag you've set earlier.

![Figure 28.19](assets/28/28.19.png)

Tap on the gramophone. And, you can preview the gramophone model in AR.

![Figure 28.20](assets/28/28.20.png)

You can see a lot of built-in features in `ARQuickLook` such as plane detection, lighting, shadow, and environment texturing, to name a few. ARQuickLook creates a universal platform experience for iOS and iPadOS users.

But, there's more, especially with commerce integration.

## Making a Merchant ID for Apple Pay with Web

Apple Pay integration on the web requires a number of prerequisites. It's not straightforward, like add a button with an Apple Pay tag and call it a day. To begin, you'll handle the non-coding logistics side of Apple Pay. In this section, you'll walk through the process of creating a merchant identifier. The merchant identifier specifies who the merchant is. You can use the merchant identifier interchangeably between native and web apps, and it never expires.

First, log in to your developer account:

![Figure 28.21](assets/28/28.21.png)

Second, under the program resources section, select **Certificates, IDs & Profiles**:

![Figure 28.22](assets/28/28.22.png)

Third, click **Identifiers** and click the **+** button:

![Figure 28.23](assets/28/28.23.png)

Fourth, select **Merchant IDs** and click **Continue**:

![Figure 28.24](assets/28/28.24.png)

Fifth, enter the merchant id's details. Give it a description and an identifier in the format of `merchant.com.domainname.appname`. Click **Continue**:

![Figure 28.25](assets/28/28.25.png)

Sixth, click **Register** to finalize your merchant id details.

![Figure 28.26](assets/28/28.26.png)

Now, you'll see something like this in your list of merchant ids.

![Figure 28.27](assets/28/28.27.png)

Great, now that you have your first piece of logistics out of the way. There are two more to go!

## Creating Your Certificate Signing Request (CSR) File

Now, you'll need to create a payment processing certificate and associate it with your merchant identifier for payment information encryption.

To create the certificate, you'll need to get a Certificate Signing Request (CSR) file from your Mac. Open **Keychain Access**.

In the upper-left corner, click **Keychain Access ▶ Certificate Assistant ▶ Request a Certificate From a Certificate Authority...**.

![Figure 28.28](assets/28/28.28.png)

First, fill in the **User Email Address** and **CA Email Address** with your email. Second, select the **Saved to disk** option. Third, enable the **Let me specify key pair information**. Fourth, click **Continue**.

![Figure 28.29](assets/28/28.29.png)

Save the **.csr** file to your computer. Click **Save**.

![Figure 28.30](assets/28/28.30.png)

In the Key Pair Information page, set the algorithm to **RSA** and key size to **2048 bits**. Click **Continue**.

![Figure 28.31](assets/28/28.31.png)

At the Conclusion page, click **Done**.

You have a CSR file generated using the RSA algorithm and with 2048 bits key size. You'll use this CSR file to create a **payment processing certificate**.

## Generating the Apple Pay Payment Processing Certificate

Open your developer account. Under the program resources section, select **Certificates, IDs & Profiles** again.

Click **Identifiers**. Click the **Merchant ID** you've created earlier.

![Figure 28.32](assets/28/28.32.png)

To integrate Apple Pay Payment Processing into your website, you'll need to agree to the Apple Pay Platform Web Merchant Terms and Conditions. Click **Review Agreement**.

![Figure 28.33](assets/28/28.33.png)

Agree to the **Terms and Conditions**.

![Figure 28.34](assets/28/28.34.png)

Under the Apple Pay Payment Processing Certificate section, click **Create Certificate**.

![Figure 28.35](assets/28/28.35.png)

Choose the **CSR** file. Click **Continue**.

![Figure 28.36](assets/28/28.36.png)

Click **Download** to download your certificate.

![Figure 28.37](assets/28/28.37.png)

The downloaded certificate should be named **apply_pay.cer**.

## Registering a Merchant Domain

In Certificates, Identifiers & Profiles, select **Identifiers**. Filter the identifiers by **Merchant IDs**. Click on your **Merchant ID**.

![Figure 28.38](assets/28/28.38.png)

Under the Merchant Domains section, click **Add Domain**.

![Figure 28.39](assets/28/28.39.png)

Enter your **domain**. Click **Save**.

![Figure 28.40](assets/28/28.40.png)

Click **Download** to download your **Apple Developer Merchant ID Domain Association** text file.

![Figure 28.41](assets/28/28.41.png)

In a new tab, open your website repository and upload the **verification text** file to your website. Then, **commit** the new changes to deploy the website.

![Figure 28.42](assets/28/28.42.png)

In addition to the text file, you'll need to edit **_config.yml** for Apple to discover your **.well-known** directory. Replace the content inside the file with the following:

```
theme: jekyll-theme-cayman

include: [".well-known"]
```

The first line of code sets the theme of your website. The second line ensures the website include and make the **.well-known** directory to the client system.

Now, your repository should look like this:

![Figure 28.43](assets/28/28.43.png)

Open back to the **Verify** page, click **Verify**. 

![Figure 28.44](assets/28/28.44.png)

Now, you've verified your domain.

## Creating an Apple Pay Merchant Identity Certificate

Specific to registering yourself as a merchant using Apple Pay, you'll create an Apple Pay Merchant Identity Certificate.

![Figure 28.45](assets/28/28.45.png)

This time, you'll need an **RSA(2048)** CSR file created from **Keychain Access** as you did earlier. The only difference here is the Key Pair Information.

![Figure 28.46](assets/28/28.46.png)

Then, upload the RSA file.

![Figure 28.47](assets/28/28.47.png)

Now, download and install Apple Pay Merchant Identity file on your computer.

![Figure 28.48](assets/28/28.48.png)

You probably don't need to make use of this file at the moment. But, it may come in handy when you need to integrate Apple Pay on an iOS/iPadOS/macOS app.

## Commerce Integration with Apple Pay

As stated earlier in the chapter, one of the clearest industry disruptors that AR is going to have is on commerce. With AR, you can bring any product into the customer's home.

At this point, you've learned how to deploy your website into the public internet. To make changes, you can either create clone your repository, make changes, and push it. Or, you can also make changes directly to the HTML file from GitHub.com.

Open **ARQuickLook.html**. Before the closing body tag, add the following code:

```
<a rel="ar" id="ApplePay" href="gramophone.usdz#applePayButtonType=plain&checkoutTitle=Gramophone&checkoutSubtitle=Gold&price=$900.00">
  <img src="gramophone.jpg">
</a>
```

Hence, your HTML file should look like this:

```
<!DOCTYPE html>
<html>
<head>
  <title>AR Quick Look</title>
</head>
<body>
  <h1>Preview a Model in AR Quick Look</h1>
  <a href="gramophone.usdz" rel="ar">
    <img src="gramophone.jpg" width=320 height=320>
  </a>
  <h2>Preview a Model with Apple Pay</h2>
  <a rel="ar" id="ApplePay" href="gramophone.usdz#applePayButtonType=plain&checkoutTitle=Gramophone&checkoutSubtitle=Gold&price=$900.00">
    <img src="gramophone.jpg">
  </a>
</body>
</html>
```

Similar to the AR button, you have the AR relationship tag. In addition, you've added an Apple Pay ID tag to indicate its role. In addition to referencing the gramophone model, you specify the Apple Pay button type, checkout title, subtitle, and price.

Commit the **changes**. Open your website in **Safari**. Tap on the **saxophone with Apple Pay** button.

You should be able to see that Apple Pay is integrated into your AR Quick Look!

![Figure 28.49](assets/28/28.49.png)

There's your 900 dollars saxophone ready for sale. Woohoo!

## Where to go from here?

Now, you can sell products and get rich off of AR Quick Look. It's time for you to make money. Go ahead and make money. Cheers.
