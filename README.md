# brick
decoration style koa server with typescript

## vscode run
1. `npm i`
2. complie typescript: `command+shift+b`
3. vscode debug `Lanuch Program` or `npm run debug` 
 
## dependencies

- use `koa-views` and `underscore` to render the view

## Usage

### controller
here is a controler demo below:
```
import { GET, POST, PUT, DEL, Validate, Render } from '../cores/Decorator';
import Joi = require('joi');

class Controller {
  @GET('/')
  async get (ctx: any) {
    return await Promise.resolve({ message: 'hello world' });
  }

  @Render('index')
  @GET('/view')
  async page (ctx: any) {
    return {  name: 'pascal' };
  }

  @Validate({
    username: Joi.string().required(),
    password: Joi.string().required(),
  })
  @POST('/login')
  async login (ctx: any) {
    return await Promise.resolve({ status: 'success' });
  }
}

export = Controller;
```

### service

extend the `core/Reposstry` can has list of function on mysql excution.