# Node-Auth

### Encryption
* In hashing, first parameter is password and second one is salt
```
const bcrypt = require('bcryptjs');

const securePassword = async (password) => {

  const hashedPassword = await bcrypt.hash(password, 10)
  const comparePassword = await bcrypt.compare(password, hashedPassword)
}

securePassword('us1234')
```

### Cookies
* Initial setup
```
const express = require("express");
const cookieParser = require("cookie-parser");

const app = express();

// middleware
app.use(cookieParser());

app.listen(3000, () => console.log(`Server is Listening on port ${3000}`));
```
* Set cookie
  * First param is cookie name and second is value
  * third one is the object
  * ```httpOnly``` if not to be accessed by client side script
  * ```Date.now()``` returns current date and add 1 second to it. Multiply it with 3600 to make it valid for 1 hour
  ```
  app.get("/set-cookie", (req, res) => {
  res.cookie("cookie-name", "cookie1", {
    expires: new Date(Date.now() + 1000 * 3600),
    httpOnly: true,
  });
  res.send("Cookie set");
  });
  ```  
* Get cookie
```
app.get("/get-cookie", (req, res) => {
  res.send(req.cookies);
});
```
* Delete cookie
```
app.get("/delete-cookie", (req, res) => {
  res.clearCookie("cookie-name");
  res.send("cookie cleared");
});
```
