
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

If we continue to look through the list of supplier searching for hints, we will encounter something like this.

![](../../Img/Pasted%20image%2020251023175033.png)

There are 5 users with that security question, all of the others it's the "no provided yet", i saved the emails in a txt file just in case.

Seeing the attack path i went to the cv upload tab to check.

![](../../Img/Pasted%20image%2020251023180012.png)

Tried to upluad a .pdf file (1mb BTW) and got an error.
Seams like i need to get the password to one of the accounts with the security question set to try and upload a CV and then get the file.

We need to check how to get the password of at least one of the users.

![](../../Img/Pasted%20image%2020251023181206.png)

Seeing as we have this convenient endpoint we are going to use it.
Fortunately a list of colors exists. (https://gist.github.com/mordka/c65affdefccb7264efff77b836b5e717)

With that list i used ffuf to check if we got a hit.

![](../../Img/Pasted%20image%2020251023182010.png)

With the new credentials we login as a suplier.

![](../../Img/Pasted%20image%2020251023182122.png)

Now we try to upload a CV again and get this.

![](../../Img/Pasted%20image%2020251023182231.png)




