# Multi Apps and multi env
```
module.exports = {
  apps: [
    {
      name: "rois",
      script: "./src/rois.js",
      env: {
        NODE_ENV: "local",
        PORT_ROIS: 3002,
        DATABASE_NAME: "db_roonline",
        DATABASE_USER: "root",
        DATABASE_PASSWORD: "",
        DATABASE_HOST: "127.0.0.1",
        DATABASE_DIALECT: "mysql",
        DATABASE_KMIIT_OPTIONAPPS_NAME: "kmiit_optionapps",
        DATABASE_KMIIT_OPTIONAPPS_USER: "kmi.champion",
        DATABASE_KMIIT_OPTIONAPPS_PASSWORD: "",
        DATABASE_KMIIT_OPTIONAPPS_HOST: "",
        DATABASE_KMIIT_OPTIONAPPS_DIALECT: "mysql"
      }
    },
    {
      name: "rhsuhu",
      script: "./src/rhsuhu.js",
      env: {
        NODE_ENV: "local",
        PORT_ROIS: 3002,
        DATABASE_NAME: "db_roonline",
        DATABASE_USER: "root",
        DATABASE_PASSWORD: "",
        DATABASE_HOST: "127.0.0.1",
        DATABASE_DIALECT: "mysql",
      }
    },
    {
      name: "scraper",
      script: "./src/scraper.js",
      env: {
        NODE_ENV: "local",
        PORT_ROIS: 3002,
        DATABASE_NAME: "db_roonline",
        DATABASE_USER: "root",
        DATABASE_PASSWORD: "",
        DATABASE_HOST: "127.0.0.1",
        DATABASE_DIALECT: "mysql",
        DATABASE_KMIIT_OPTIONAPPS_NAME: "kmiit_optionapps",
        DATABASE_KMIIT_OPTIONAPPS_USER: "kmi.champion",
        DATABASE_KMIIT_OPTIONAPPS_PASSWORD: "",
        DATABASE_KMIIT_OPTIONAPPS_HOST: "",
        DATABASE_KMIIT_OPTIONAPPS_DIALECT: "mysql"
      }
    }
  ]
};

```
