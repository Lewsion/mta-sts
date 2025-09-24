<div align="center">

# MTA-STS Policy Hosting on GitHub Pages

**A simple and effective template for hosting your MTA-STS policy file using GitHub Pages.**

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/Lewsion/mta-sts/blob/gh-pages/LICENSE.md)
[![GitHub Pages](https://img.shields.io/badge/GitHub-Pages-green.svg)](https://lewsion.github.io/mta-sts/)

</div>

---

## 📖 Table of Contents

- [About MTA-STS](#about-mta-sts)
- [🚀 Getting Started](#getting-started)
- [✅ Prerequisites](#prerequisites)
- [🔧 Configuration](#configuration)
- [🧪 Validation](#validation)
- [🤝 Contributing](#contributing)
- [📝 License](#license)
- [📧 Author](#author)

---

## About MTA-STS

**MTA Strict Transport Security (MTA-STS)** is a security standard that helps to protect email delivery from downgrade and man-in-the-middle attacks. It allows mail servers to declare their ability to receive TLS-secured connections and to specify whether sending mail servers should refuse to deliver to MX hosts that do not offer TLS with a trusted server certificate.

This template provides a straightforward way to host your MTA-STS policy file on GitHub Pages, making it easy to implement this important security feature for your domain.

---

## 🚀 Getting Started

To get started, you can use this repository as a template to create your own MTA-STS policy hosting repository.

1. Click the [**Use this template**](https://github.com/Lewsion/mta-sts/generate) button to create a new repository based on this template.
2. Choose a name for your new repository (e.g., `mta-sts.yourdomain.com`).

---

## ✅ Prerequisites

Before you can use this template, you will need:

- A GitHub account.
- A domain name for which you want to enable MTA-STS.
- Access to your domain's DNS records.

---

## 🔧 Configuration

1. **Customize the MTA-STS Policy:**
    - Edit the `.well-known/mta-sts.txt` file to match your mail server configuration.
    - You will need to update the `mx` values to match your mail server's MX records.

2. **Set up GitHub Pages:**
    - In your new repository, go to **Settings > Pages**.
    - Under **Branch**, select `gh-pages` as the source and click **Save**.
    - If you are using a custom domain, enter your custom domain name in the **Custom domain** field and click **Save**.

3. **Configure DNS Records:**
    - Create a `CNAME` record for `mta-sts.yourdomain.com` that points to `<your-username>.github.io`.
    - Create a `TXT` record for `_mta-sts.yourdomain.com` with the following format:

        ```dns
        _mta-sts.yourdomain.com. IN TXT "v=STSv1; id=<unique-id>"
        ```

        - Replace `<unique-id>` with a unique identifier. It is recommended to use the current date and time (e.g., `20250924T120000Z`).
        - **Important:** You must update the `id` value in your DNS record whenever you make changes to your `mta-sts.txt` file.

4. **(Optional) Enable TLS Reporting:**
    - Create a `TXT` record for `_smtp._tls.yourdomain.com` to enable TLS reporting:

        ```dns
        _smtp._tls.yourdomain.com. IN TXT "v=TLSRPTv1; rua=mailto:<reporting-email-address>"
        ```

        - Replace `<reporting-email-address>` with the email address where you want to receive TLS reports.

---

## 🧪 Validation

After you have configured your MTA-STS policy, you can use the following tools to validate your setup:

- [MXToolBox MTA-STS Lookup](https://mxtoolbox.com/mta-sts.aspx)
- [Hardenize](https://www.hardenize.com/)

---

## 🤝 Contributing

Contributions are welcome! If you have any suggestions or improvements, please feel free to open an issue or submit a pull request.

---

## 📝 License

This project is licensed under the MIT License. See the [LICENSE.md](httpshttps://github.com/Lewsion/mta-sts/blob/gh-pages/LICENSE.md) file for details.

---

## 📧 Author

This template was created by **Julian Pawlowski** and adapted by **ENDRENCE LETERNET**.

- **Julian Pawlowski:** [julian.pawlowski.me](https://julian.pawlowski.me/) | GitHub [@jpawlowski](https://github.com/jpawlowski)
- **ENDRENCE LETERNET:** [lewsion.com](https://lewsion.com) | GitHub [@Lewsion](https://github.com/Lewsion)
