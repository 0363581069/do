let body = JSON.parse($response.body);
body.data.is_premium = true; // Mở khóa template premium
body.data.watermark = false;  // Loại bỏ dấu kiểm của template premium. Cần thiết để dùng template premium
if (body.data.hasOwnProperty("resources")) {
    for (let i = 0; i < body.data.resources.length; i++) {
      body.data.resources[i].is_premium = true;
      body.data.resources[i].watermark = false;

      // Kiểm tra nếu resource có sticker
      if(body.data.resources[i].hasOwnProperty("stickers")){
          for (let j = 0; j < body.data.resources[i].stickers.length; j++)
          {
              body.data.resources[i].stickers[j].is_premium = true;
                body.data.resources[i].stickers[j].watermark = false;
          }
      }
      // Kiểm tra nếu resource có font
      if (body.data.resources[i].hasOwnProperty("fonts")) {
        for (let j = 0; j < body.data.resources[i].fonts.length; j++){
            body.data.resources[i].fonts[j].is_premium = true;
              body.data.resources[i].fonts[j].watermark = false;
        }
      }
        // Kiểm tra nếu resource có effect
        if (body.data.resources[i].hasOwnProperty("effects")) {
        for (let j = 0; j < body.data.resources[i].effects.length; j++){
            body.data.resources[i].effects[j].is_premium = true;
             body.data.resources[i].effects[j].watermark = false;
        }
      }

      // Kiểm tra nếu resource có filter
        if (body.data.resources[i].hasOwnProperty("filters")) {
        for (let j = 0; j < body.data.resources[i].filters.length; j++){
            body.data.resources[i].filters[j].is_premium = true;
            body.data.resources[i].filters[j].watermark = false;
        }
      }
    }
}
$done({ body: JSON.stringify(body) });

