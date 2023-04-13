Firefox is a popular browser that is used to access the Internet. For this particular check we will run the SCAP Compliance checker we will see if the browser is fit to use and it has no vulnerabilities that will affect the Confidentiality, Intergrity and Avaliability. 

![mf](https://user-images.githubusercontent.com/93686063/231775409-6d301a21-bb8a-4656-85b9-45a9aa36abf4.JPG)

![mf1](https://user-images.githubusercontent.com/93686063/231777289-a8e259e5-679b-4500-a886-54301ffa992a.JPG)

Since there are a lot of errors that we need to fix, we will be using the LGPO tool which automates a lot of these processes. 

`LGPO.exe is a command-line utility that is designed to help automate management of Local Group Policy. It can import and apply settings from Registry Policy(Registry.pol) files, security templates, Advanced Auditing backup files, as well as formatted "LGPO text" files and Policy Analyzer ".PolicyRules"XML files.` 

We will now go to the DoD Cyber Exchange website and download the Group Policy Objects(GPOs). The latest ones that we have are from January 2023.

![gpo](https://user-images.githubusercontent.com/93686063/231779553-acd4abf7-01a6-4d56-bd73-c3d2efab4e01.JPG)

We will first copy the `.admx` and `.adml` files in our C:\Windows\PolicyDefinitions. 

`Before we run the LGPO tool for Firefox, we need to make sure that we copy the Administrative Templates in Group Policy. ADMX files are XML text files that describe what you see under Computer Configuration\Policies\Administrative Templates and User Configuration in Group Policy Editor. Once these files are stored mostly under Policy Definitions in the Windows Folder, the only time they are read or considered are when you are editing GPOs in GP Editor. When you expand the Administrative Template node, and you see all of those folders, sub-folders and policy items those correspond to GP Editor reading each ADMX File it finds.` 


![gpo1](https://user-images.githubusercontent.com/93686063/231783250-9ca72f45-d19b-4ad7-b2e3-8837f5ff01c2.JPG)

We will also need to copy the `.adml` files which are located in the en-US folder. 


![gpo2](https://user-images.githubusercontent.com/93686063/231783707-fc45fdea-e613-4a5e-97f3-1a0a98c841a3.JPG)


Once we are inside the LGPO folder in an elevated Command prompt, we will use the LGPO.exe command. The LGPO.exe applies the contents of the supplied input files to local policy. We will be using the `/g path` which `imports the settings from one or more Group Policy backups anywhere under the directory specified by path`. 

![gpo3](https://user-images.githubusercontent.com/93686063/231785524-faaca7c0-f844-4c13-ab45-76c01a3005ad.JPG)

We will get the following result, now that we have the following result, we will do a `gpupdate /force` in order to update the policies. 

![gpo4](https://user-images.githubusercontent.com/93686063/231786713-ea3f8a42-5294-4db1-a3ab-274d0f1784fd.JPG)

Now that we have updated the policies and used the LGPO tools, we can see a different result and a far better result for the same application. We are well above GREEN on the compliance and we can now run the Stig viewer to see if we can make any changes manually. 

![gpo5](https://user-images.githubusercontent.com/93686063/231787214-fdedb6f6-79ee-4434-ab71-b0bc825baa74.JPG)

![image](https://user-images.githubusercontent.com/93686063/231787484-0aaca316-4d0e-4d64-ad15-ef5a8e523dfe.png)

