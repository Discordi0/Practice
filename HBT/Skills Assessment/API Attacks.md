
## [Scenario](https://academy.hackthebox.com/beta/module/268/section/3071#scenario)

After reporting all vulnerabilities in versions v0 and v1 of `Inlanefreight E-Commerce Marketplace`, the admin attempted to patch all of them in v2:

![Swagger UI for Inlanefreight E-Commerce Marketplace API version v2. Security vulnerabilities in v1 have been addressed. Sections include Authentication, Customers, Products, Roles, Supplier-Companies, and Suppliers.](https://academy.hackthebox.com/storage/modules/268/Skills_Assessment_Image_1.png)

However, new junior developers have implemented additional functionalities in v2, and the admin is concerned that they may have introduced new vulnerabilities. Assess the security of the new web API version and apply everything you have learned throughout the module to compromise it.



## Questions

### Q1: Submit the contents of the flag at '/flag.txt'.

#### A: 

First we need authenticate with the provided credentials.

![](../../Img/Pasted%20image%2020251023174352.png)

![](../../Img/Pasted%20image%2020251023174414.png)

![](../../Img/Pasted%20image%2020251023174428.png)

With that, we need to check the roles assigned to the acc.

![](../../Img/Pasted%20image%2020251023174508.png)

Getting a look at all suppliers we can see a posible attack path. ( the professionalCVPDFFileURI attribute)

![](../../Img/Pasted%20image%2020251023174707.png)

