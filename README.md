# Linking GitHub Pages with a Custom Domain (trocstop.com)

This guide explains how to link your GitHub Pages site to your custom domain name using Namecheap. In this example, we will use the domain `trocstop.com` as our custom domain.

## Prerequisites

1. A GitHub repository with a GitHub Pages site set up (e.g., `username.github.io` or `organisation.github.io`).
2. A custom domain name registered with Namecheap (e.g., `trocstop.com`).

## Step 1: Configure GitHub Pages for a Custom Domain

1. **Navigate to Your Repository:**
   - Go to the GitHub repository that is serving your GitHub Pages site.

2. **Open Repository Settings:**
   - Click on the **Settings** tab in your repository.

3. **Scroll to GitHub Pages:**
   - Under the **Code and automation** section, find the **Pages** link.

4. **Set the Custom Domain:**
   - In the **Custom domain** field, enter your domain name (e.g., `www.trocstop.com`).
   - Make sure the **Enforce HTTPS** checkbox is checked. This will ensure secure connections.

5. **Create a `CNAME` File (Optional but Recommended):**
   - In your repository’s root directory, create a file named `CNAME`.
   - Inside the `CNAME` file, add your custom domain name, e.g.:
     ```
     www.trocstop.com
     ```

## Step 2: Set Up DNS Records on Namecheap

Now we need to configure the DNS settings on Namecheap to point your domain to GitHub Pages.

1. **Log in to Namecheap:**
   - Go to [namecheap.com](https://www.namecheap.com) and log in to your account.

2. **Navigate to Domain List:**
   - From the dashboard, click on **Domain List** on the left sidebar.
   - Find your domain (e.g., `trocstop.com`) and click **Manage**.

3. **Update DNS Settings:**
   - In the **DNS** section, set **Nameservers** to **Namecheap Basic DNS** if it's not already set.

4. **Add the Following DNS Records:**

   - Under the **Advanced DNS** tab, add the following records:

   | Record Type | Host           | Value                          | TTL  |
   |-------------|----------------|--------------------------------|------|
   | CNAME       | www            | `username.github.io`           | Automatic |
   | A Record    | @              | `185.199.108.153`              | Automatic |
   | A Record    | @              | `185.199.109.153`              | Automatic |
   | A Record    | @              | `185.199.110.153`              | Automatic |
   | A Record    | @              | `185.199.111.153`              | Automatic |

   **Explanation:**
   - The `CNAME` record points `www.trocstop.com` to your GitHub Pages site.
   - The `A` records ensure that `trocstop.com` (without `www`) points to the same GitHub Pages site.

5. **Save Changes** and wait for the DNS settings to propagate. This may take a few minutes to several hours.

## Step 3: Verify the Setup

1. **Visit Your Domain:**
   - Open a browser and visit `www.trocstop.com`. It should display your GitHub Pages website.
   - Try visiting `trocstop.com` as well, to ensure both the `www` and root domains work.

2. **Verify HTTPS:**
   - Once GitHub Pages sets up HTTPS (this may take a few minutes), ensure that your website is accessible via HTTPS (`https://www.trocstop.com`).

## Troubleshooting

- **DNS Propagation Time:** Changes to DNS records may take some time to propagate. You can check DNS status using online tools like [WhatsMyDNS](https://www.whatsmydns.net/).
- **HTTPS Issues:** If HTTPS is not working, ensure that the **Enforce HTTPS** option is checked in the GitHub Pages settings and that DNS records are properly configured.

## Resources

- [GitHub Pages Custom Domain Documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Namecheap DNS Setup](https://www.namecheap.com/support/knowledgebase/article.aspx/9776/2237/how-to-set-up-dns-records-for-your-domain-in-namecheap)

That’s it! You’ve successfully linked your GitHub Pages site with the custom domain `trocstop.com`.
