# Zabbix SSO with Microsoft Entra ID 
## Prerequities:
* Your zabbix must have active SSL certificates
### Step:1 
* Login to azure account and navigate to Enterprice Application.
  
  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/66f59c6f-e5bb-4b4d-971f-3a6033134485)


* Now create a new applicaton and give appropriate name and click on Create.

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/01b35b01-e765-4a83-ac1b-a1c06b63ffaa)


### Step:2
* Now Go to user and group option and select the users for the SSO.

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/d6514973-6570-4ba1-85ed-525df87249ba)


* Navigate to Single Sign On and then select SAML option

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/f3ac9826-610c-4a81-b046-baf56c9d6a93)

### Step:3
* Now click on Edit button of Basic SAML Configuration in right corner.
  
  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/2719de85-5586-4624-86b7-d647395a28d0)

  
* Now click on add identifier and give Entity ID: **zabbix.telemetrics.tech1** and also add the reply URL: 
  https://zabbix.telemetrics.tech:5121/index_sso.php?acs (you can find this in the given directory: /usr/share/zabbix)

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/85ae1ffd-188e-44a4-b57d-0baa7f541e94)

* Save the configuration that we have done

### Step:4 
* Now navigate to second option Attribute & Claima and click on edit

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/fffcd8fa-67a5-4486-b140-fb3c0aea4c33)

* Now Delete all the addition claims

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/821489d9-3ef5-4985-8c21-779b76a7eb7f)

* After deleting addition claims add two new claims by clicking Add new Claim and then in thr Name field enter name and in 
  source attribute select user.userprinciplename.

* Now add another new claim and this time in the name field enter alias and in source attribute: user.userprinciplename.
  
  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/edddb8ce-a998-4b4e-8cd2-6eb7acecb516)
  
### Step:5 
* Now look on the 3rd option and from there download certificate (Base64) and save it as idp.crt

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/8f1284b3-8d19-4d31-ba84-ce77016994d1)
  
* now in the next option Set up Zabbix there are two values 1. Login Url 2. Microsoft Entra Identifier.
* Which are important so we need to note it down somewhere.
  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/6fe53f81-1c26-441e-b271-9807659373fe)

### Step:6 
* Upload the downloaded certificates in given given directory: /usr/share/zabbix/conf/certs
* Now navigate to zabbix UI and then User > Authentication > SAML Settings and fill up following values:
   1. IdP entity ID : (Microsoft Entra Identifier that we note down earlier)
   2. SSO service URL : (Login Url that we note down earlier )
   3. Username attribute : alias
   4. SP entity ID : zabbix.telemetrics.tech1
   5. Update the setting.

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/b4b81d01-99ad-4060-bfd5-347d247fef41)

### Step:7 
* Navigate to your azure portal and go to Entra ID > Users copy user's principle name
* Now in the zabbix create create new user with same user principle name that we copy earlier and add the user in zabbix 
  Administrator group and navidate to Permission and give role to the user.

  ![image](https://github.com/Krunal2906/ZABBIX-SSO/assets/88182302/f30863e6-d7a7-4a96-b02c-cec2a9a3b2c4)

* Now you can do the sso on your zabbix.


  
