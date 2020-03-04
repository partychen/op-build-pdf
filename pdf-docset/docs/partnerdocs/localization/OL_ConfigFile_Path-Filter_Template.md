# OL Configuration File - Path-Filter Template

```
{
  "filters": [
    {
      "files": [ "docset1/*.md", "docset2/*.md" ],
      "priorities": [
        {
          "priority": "ht",
          "locales": [ "de-de", "ja-jp", "zh-tw" ],
	"type": "HT"
        },
        {
          "priority": "mt",
          "locales": [ "ru-ru", "pl-pl", "ko-kr" ],
	"type": "MT"
        }

      ]
    }
  ],
  "includeDependencies": true,
  "autoPush": true,
  "xliffVersion": "1.2"
}
```

* Change the files and priorities as you required
* Add more filter for different translation requirement for different folders and different locales
* Use [https://jsonformatter.curiousconcept.com/](https://jsonformatter.curiousconcept.com/) to validate your json file
