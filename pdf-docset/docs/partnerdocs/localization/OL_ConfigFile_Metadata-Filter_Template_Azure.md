# OL Configuration File - Metadata-Filter Template(Azure used)

```
{
  "filters": [
    {
      "metadata": {
        "ms.topic": [ "hero-topics", "getting-started-topics" ]
      },
      "priorities": [
        {
          "priority": "high",
          "locales": [ "de-de", "ja-jp", "zh-tw", "ru-ru", "pl-pl", "ko-kr" ],
	"type": "MT"
        }
      ]
    },
    {
      "files": [ "**/*.md" ],
      "priorities": [
        {
          "priority": "ht",
          "locales": [ "de-de", "ja-jp", "zh-tw", "ru-ru", "pl-pl", "ko-kr" ],
	"type": "HT"
        }
      ]
    }
  ],
  "includeDependencies": true,
  "autoPush": true,
  "xliffVersion": "1.2"
}
```


* Change the metadata and priorities as you required
* Change the files and priorities as you required
* Add more filter for different translation requirement for different path/metadata and different locales
* Use [https://jsonformatter.curiousconcept.com/](https://jsonformatter.curiousconcept.com/) to validate your json fil

