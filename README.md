# Debugging: 

* app.js
   * Added `require('dotenv').config()` to line 6 - allows use of .env for MONGODB_URI
   * Moved `const app = express(); and mongoose.connect` from line 39 to line 11 - `app` and db instantiation has to occur before middleware
   * Moved `app.use('/', blogRouter);` from line 35 to line 30 - moved above 404 catcher

* models/Blog.js 
   * corrected exported module (`Blog` -> `module.exports = mongoose.model('Blog', BlogSchema)`)
   * removed `unique` property from line 5 (author) - this would prevent creating blog under the same author

* routes/blog.js
   * Line 2: Changed `const router = express.Route();` -> `const router = express.Router();`
   * corrected name of the exported module (`route`-> `router`)

* controllers/BlogController.js
   * In `createBlog` and `updateBlog` functions changed following: 
      * `name` -> `title;`
      * `writer` -> `author;`
      * `about` -> `subject;`
      * `description;` -> `article;`
   * These changes were made to mimic Blog model keys