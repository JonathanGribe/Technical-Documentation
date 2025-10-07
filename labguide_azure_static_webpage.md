# Deploying a Static Web Page through Azure Blob Storage

## Introduction
In this lab, you will learn how to host a simple static website using **Azure Blob Storage**. Azure Blob Storage is a cloud-based service that allows you to store files such as HTML, CSS, and JavaScript, and make them accessible over the internet. By the end of this exercise, you will have a working static web page hosted directly from Azure.

## Learning Objectives
By completing this lab, you will:
- Learn how to create an **Azure Storage Account** and a **Blob container**.
- Configure the container to support **static website hosting**.
- Upload web files (HTML, CSS, JavaScript) to Blob Storage.
- Access your static web page through a public URL.

## Prerequisites
- None. This lab assumes no prior knowledge of Azure.

## Environment
- **Microsoft Azure Portal**: [https://portal.azure.com](https://portal.azure.com)

---

## Step-by-Step Instructions

### 1. Create a Storage Account
1. Sign in to the **Azure Portal**.
2. In the left-hand menu, select **Create a resource**.
3. In the search bar, type **Storage account** and select it.
4. Click **Create**.
5. Under the **Basics** tab, fill in the following:
   - **Subscription**: Choose your available subscription.
   - **Resource group**: Select an existing group or click **Create new**.
   - **Storage account name**: Enter a unique name (lowercase letters and numbers only).
   - **Region**: Choose a region close to you.
   - **Performance**: Leave as **Standard**.
   - **Redundancy**: Leave as **Locally-redundant storage (LRS)**.
6. Click **Review + Create**, then click **Create** again to deploy the storage account.

### 2. Enable Static Website Hosting
1. Once deployment is complete, go to your new **Storage account**.
2. In the left-hand menu, under **Data management**, select **Static website**.
3. Click **Enable**.
4. In the **Index document name** field, type `index.html`.
5. (Optional) In the **Error document path** field, type `error.html`.
6. Click **Save**.
7. Note the **Primary endpoint URL** displayed. This will be the public address of your website.

### 3. Create a Blob Container
1. In the storage account menu, select **Containers**.
2. Click **+ Container**.
3. Enter a name for your container (e.g., `webfiles`).
4. Set **Public access level** to **Blob (anonymous read access for blobs only)**.
5. Click **Create**.

### 4. Upload Website Files
1. Open your new container.
2. Click **Upload**.
3. In the **Upload blob** panel, click **Browse for files** and select your `index.html` file (and any supporting files such as CSS or images).
4. Click **Upload**.

---

## Verification
- Return to the **Static website** section of your storage account.
- Copy the **Primary endpoint URL**.
- Paste it into a web browser.
- If successful, your `index.html` page will load as a live website.

---

## Troubleshooting
- **Website does not load**:
  - Ensure you uploaded `index.html` to the correct container.
  - Confirm that **Static website hosting** is enabled.
- **Access denied error**:
  - Check that the container’s **Public access level** is set to **Blob**.
- **Changes not visible**:
  - Clear your browser cache or refresh the page.

---

## Next Steps
Once you have a working static website, you can explore:
- Adding **custom domains** to replace the default Azure URL.
- Securing your site with **HTTPS** using Azure-managed certificates.
- Using **Azure Content Delivery Network (CDN)** to improve performance.
- Expanding your site with additional HTML, CSS, and JavaScript files.
