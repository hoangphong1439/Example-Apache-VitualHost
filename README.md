# Example-Apache-VitualHost

<VirtualHost 141.211.175.38:80>
  ServerName user01.ws.umdl.umich.edu  

  DocumentRoot          /l1/workshop/user01/dlxs/web  
  ScriptAlias   /cgi/   /l1/workshop/user01/dlxs/cgi/  
  SetEnv DLXSROOT       /l1/workshop/user01/dlxs<br>  
  # optional
  SetEnv DLXSDATAROOT   /l1/workshop/user01/dlxs
  SetEnv REMOTE_USER    user01  
  UnsetEnv DLPS_DEV
  # optional  
  SetEnv DLPS_DEV       user01

<Directory /l1/workshop/user01/dlxs/cgi/b/bib>   
  SetEnv AUTHZD_COLL  :    
  SetEnv PUBLIC_COLL  :amverse-bib:samplebc:
</Directory>  

<Directory /l1/workshop/user01/dlxs/cgi/i/image>    
  SetEnv AUTHZD_COLL  :   
  SetEnv PUBLIC_COLL  :sampleic:workshopic:
</Directory>

<Directory /l1/workshop/user01/dlxs/cgi/t/text
  SetEnv AUTHZD_COLL  :
  SetEnv PUBLIC_COLL  :moajrnl:moa:sampletc:workshoptc:
</Directory> 

<Directory "/l1/workshop/user01/dlxs/cgi/c/collmgr">
  AuthName "DLXS collection management"
  AuthType Basic

  AuthUserFile conf/htpasswd.dlxs

  Require user dlxsadm
</Directory>
</VirtualHost> 
