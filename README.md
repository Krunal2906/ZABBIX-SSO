       Zabbix SSO with Microsoft Entra ID

            Step 1: Check SSL certificate
            Step 2: Go to Azure portal
	Step 3: Enterprise application and Create New Application



            Step 4: Give app name
Step 5: Once the application is created, add a user or group to the application. 

![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/765a62ca-e90e-4fb0-b172-9eb37f9155d5)




Step 6: Go to SSO, and select SAML





Step 7: Go to Basic SAML Configuration 


           -Give Entity ID (xyz.com):xxxx/index_sso.php?acs
            (You can find this in /usr/share/zabbix)
	Step 8: Save the Basic SAML configuration
	Step 9: Attributes & Claims – Delete all the additional claims
           Step 10: Add two new claims

1.	Name: name
Source attribute: user.userprincipalname
2.	Name: alias
Souece attribute:user.userprincipalname
Step 11: Download Certificate (Base 64)
                             Save the certificate as “idp.crt”
      

           Step 12: Upload the idp.crt in – cd/usr/share/Zabbix/conf/certs

         Step 13: Set up Zabbix


                        
                         Copy Microsoft Entra Identifier
                         Paste - Entity ID in Zabbix
                         Copy Login URL
                         Paste – SSO service url
                         Username attribute – alias
                         Sp Entity Id – xyz.com
                         Click Update
 Step 14: Go to Azure Portal – Entra ID – Users
                         Copy user principal name


                         Create new user in Zabbix with the same principal name
                         (Groups : Zabbix admin)
                         Add Role
     Step 15:  Login with SSO
                       

                         
            



