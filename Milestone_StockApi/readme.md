# STOCK API

[live on render.com](https://fullstack-stockapp.onrender.com)

### Deployment:

- BE-FE beraber deploy edileceği için frontend kısmındaki useAxios dosyasındaki path değiştirildi.
- FE' de "$npm run build" yapıldı.
- build ile gelen dosyalar BE'de public klasörü açılarak altına kopyalandı.
- BE index.js'e yapılan eklemeler:
  _ const path = require("path");
  _ app.use(express.static(path.join(**dirname, "public")));
  _ "/api/v1/documents" //swagger ve redoc için pathler düzeltildi.// "/api/v1/documents/swagger"
  _ app.use("/api/v1", require("./src/routes"));
  _ app.get("_", (req, res) => {
  res.sendFile(path.resolve(**dirname, "./public", "index.html"));
  });
  _ app.use("*", (req, res) => {
  res.status(404).json({ msg: "not found" });
  }); 
  _ if (process.env.NODE_ENV == "development") {
  require("./src/configs/sync")();
  }
- render.com'da web service oolarak deploy edildi.

### ERD:

![ERD](./erdStockAPI.png)
