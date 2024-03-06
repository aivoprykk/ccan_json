CCAN JSON for ESP-IDF
==================
CCAN JSON is a basic json library for ESP32 devices licensed mostly under MIT.
(See caption "License" for details.)

Usage
-----
Clone this repository or add it as a submodule into your components directory.
Add the module as a requirement to your main module, or other modules.

Example Code
------------
```c
#include "esp_log.h"
#include "json.h"

void app_main(void)
{
    const char * json ="{\"test\":\str\""}";
    JsonNode *root = 0;
    if (!json_validate(json)) {
        ESP_LOGE(TAG, "Bad json: %s", json);
        return 0;
    }
    root = json_decode(json);
    if (!root) {
        ESP_LOGE(TAG, "Parser error: %s", json);
        return 0;
    }

    int changed = 0;
    JsonNode *name = 0, *value = 0;
    const char *var = 0;
    if (!str) {
        name = json_find_member(root, "test");
        if (name && name->tag == JSON_STRING)
            var = name->data.string_;
    } else {
        // name = str;
        value = json_find_member(root, str);
        // value = name;
        var = str;
    }
    
}
```

License
-------
This repository contains a lot of code I have written which is licensed under
MIT, however there are sections modified from the BME280 datasheet which is
unclearly licensed.

The unclearly licensed section is clearly marked with two comments. Any code
between `// HERE BE DRAGONS` and `// END OF DRAGONS` contains modified versions
of the Bosch Sensortec code.

Please take note of this in production.