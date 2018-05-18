Update: April 5, 2018



# Introduction

This lab walks you through some examples using the Oracle Object Storage. You will create and interact with Object Storage buckets using a Ravello virtual machine with Oracle Linux.



**Please direct comments / questions to: Christian Yarros (christian.yarros@oracle.com).**

## Objectives

-	Provision an Oracle Linux machine
-	Create object buckets in Oracle Cloud Infrastructure console
-	Download OCI CLI and use it to interact with object storage.


## Required Artifacts
- The following lab requires:
    - an Oracle Public Cloud trial account.
    - a Ravello Systems account.
    - PuTTY software


# OCI Object Storage
Oracle Object Storage is a web-based interface that provides the ability to accelerate a broad range of high performance applications with your choice of high IO block storage, and durable, high-throughput object storage.


### **STEP 1**: Go to [OCI console](https://console.us-phoenix-1.oraclecloud.com).


### **STEP 2**: Log in to your Oracle Cloud Infrastructure Console with the following credentials provided by your Oracle Cloud administrator.

- Enter the Cloud Tenant provided by your Oracle Cloud administrator in the **Cloud Tenant** field and select **Continue**.

- **Username**: &lt;username&gt;

- **Password**: &lt;password&gt;


### **STEP 3**: Enter the Object Storage Console.
- Select the **Storage** tab in the navigation bar

  ![](./images/200/2.png)

- Select **Object Storage** in the side menu

  ![](./images/200/3.png)

### **STEP 4**: Select Create Bucket to create the storage bucket to upload your source files into. You will later copy this data into database tables in your Autonomous Data Warehouse Cloud.

- Select **Create Bucket**


- Enter the following information:

  -   **Bucket Name** - &lt;yourname&gt;OS. &lt;&lt; Prefix your storage bucket name with a unique name (you can use your name, for example), e.g. JackOS. Since all users will be using the same cloud account, it is important that you use a unique bucket name.

  -   **Storage Tier** - Standard &lt;&lt; Do not select Archive as this tier will store its data differently.

Select **Create Bucket**.



### **STEP 5**:  Upload files to your storage bucket.

Get a file ready for upload. Object Storage can handle just about any type of file. If you do not have any files to work with, feel free to get this sample file here.

- Download Insurance.csv from github repository:
    - Open the following link in a new tab: [Insurance.csv](https://raw.githubusercontent.com/unofficialoraclecloudhub/autonomous-campaign/master/workshops/adwc-trialcampaigns/objectstorage/Insurance.csv)
    - Right Click anywhere on browser page and select **Save as...**
    - Save file
    - Go back to OCI Object Storage Console


- Select your bucket name in the list of buckets. i.e. &lt;yourname&gt;OS

  ![](./images/200/6.png)

- Upload the file.

  - Select **Upload Object**

  ![](./images/200/7.png)

  - Select **Browse** and select your file.

  ![](./images/200/8.png)

  - Select **Upload Object** and the popup will disappear.


### Next Steps

  - Sometimes the browser console doesn't provide enough functionality. In that case, Oracle provides the Oracle Cloud Infrastructure Command Line Interface. In the next steps, we will set up an Oracle Linux machine through Ravello and interact with Object Storage via OCI CLI.


# Ravello

With Oracle Cloud Infrastructure Ravello Service, you can deploy your existing VMware or KVM based data center workloads on any public cloud such as Oracle Cloud, Amazon Web Services (AWS), and Google Cloud, as-is, without any modification to the virtual machines, network, or storage.

This is useful for small workshops like this, because it takes very little time to spin up an Oracle Linux Machine that you can work in.

### **STEP 1**: Login to [Ravello](login.ravellosystems.com)

### **STEP 2**: Create an application

- Select Create Application in the top right of the page.
- Name it whatever you'd like. For example, ObjectStorageDemo.
- Once it's created, select the application name in the list.

  ![](image)

### **STEP 3**: Publish Application

- On the Application page, drag the Oracle 12cR1 virtual machine into the canvas.

  ![](image)

- Select **Publish**
- In the popup window, enter the default form fields and select **Publish**
- After a few moments, the Virtual Machine box will be ready.


### **STEP 4**: Record IP address

- When you've selected a VM in the canvas, information about the VM will be displayed on the right.
- In the Summary section, find the IP address of this virtual machine. This will be used to connect via Putty.

  ![](image)


### **STEP 5**: Open a Putty session in your VM

If you don't already have PuTTY, feel free to download it [here.](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

- In Putty, enter the IP address of your Oracle Linux virtual machine that you created in Ravello and select **Open**
- Make sure you're not in VPN or Ethernet to connect through putty. use clear-guest or a similar network
-	Sign in as **oracle**, password is **ravello**


### Next Steps

  - Next we will interact with Object Storage using OCI CLI.


# Oracle Cloud Infrastructure Command Line Interface

The CLI is a small footprint tool that you can use by itself, or with the Console to complete Oracle Cloud Infrastructure tasks. The CLI provides much the same functionality as the Console and includes additional advanced commands. Some of these commands, such as the ability to run scripts, extend the Console's functionality.

### **STEP 1**: Install Oracle Cloud Infrastructure Command Line Interface


-	To Install OCI CLI, run the following command in your putty session:

```

  bash -c "$(curl -L https://raw.githubusercontent.com/oracle/oci-cli/master/scripts/install/install.sh)"

```

### **STEP 2**: Configure OCI CLI

-	To use OCI CLI Commands you must create a public key and add it to your Oracle Cloud Infrastructure user settings. This can be completed using the following command:

```

  oci setup config

```

- Follow the prompts. If you are unsure of what you should enter, most is available in the browser OCI console (i.e. Object Storage)

#### Refer to this guide:

**USER OCID** = located on your user information page in OCI console

**TENANCY OCID** = Located in the bottom left of your OCI console

**KEY_FILE** = this is the path to your private key that you configured during oci setup

**COMPARTMENT ID** = you can find this in Identity -> Compartments -> <your-compartment> -> select **Show** under OCID

**REGION** = located at the top of the OCI Console next to tenancy


### **STEP 3**: Provide Oracle Object Storage with the OCI CLI public key that was created in oci setup config.

Now that you have a private / public key combo , you must add it to OCI Console:

- Add it to your OCI user settings:
  - Go to your Oracle Cloud Infrastructure console and select User Settings on the user dropdown in the top right corner.
  - Select Add Public Key and add the public key you copied from the command line interface.
- You should now be able to access your object storage from the command line.

- If for whatever reason you still cannot connect, try running the following command and follow the prompts:

```
oci setup autocomplete
```


### **STEP 4**: Interact with object storage.

Now that you have setup OCI CLI, try your hand at moving files in and out of object storage.


-	Here is a list of several OCI commands:

**Downloading Object**
```

oci os object get -ns <your-namespace> -bn <your-bucketname> --name <file-name> --file <file-name>

```

**Uploading Object**
```

 oci os object put -ns <your-namespace> -bn <your-bucketname> --name <file-name> --file - <<< '<file name>'

```

**Listing buckets**
```

oci os bucket list -ns <your-name-space> --compartment-id <your-compartment-id>

```

**Listing Objects in bucket**
```

oci os object list -bn <your-bucketname> -ns <your-namespace>

```

**Bulk Download**
```

oci os object bulk-download -ns <your-name-space> -bn <your-standardBucket> --download-dir <your-directory>

```

**Bulk Upload**
```

oci os object bulk-upload -ns <your-namespace> -bn <your-archiveBucket> --src-dir <your-directory>

```


# What you Learned

How to:
-	Provision an Oracle Linux machine
-	Create object buckets in Oracle Cloud Infrastructure console
-	Download OCI CLI and use it to interact with object storage.


# Want to Learn More?

- [Object Storage Overview](https://docs.us-phoenix-1.oraclecloud.com/Content/Object/Concepts/objectstorageoverview.htm)

- [The Power of Oracle Cloud Infrastructure CLI](https://docs.us-phoenix-1.oraclecloud.com/Content/API/Concepts/cliconcepts.htm)
