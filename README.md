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
