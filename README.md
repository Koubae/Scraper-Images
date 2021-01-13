Scraper Image
=======================

Simple Google Image Scraper.

#### Disclaimer: The Original implementation of Magic is fully credited to @AdamHupp.

I modified it in order to better suit the purpose of this simple web scraper.
The Package can be found at [Here](https://pypi.org/project/python-magic/). 

* [Repository](https://github.com/ahupp/python-magic)

The Actual Script was taken from [here](https://github.com/julian-r/python-magic/blob/master/magic/magic.py) which as fixes for Windows 64-bit.



Documentation
-------------

### 1. Installation


##### Window 64-bit!!!

If you are using a 64-bit build of python, you'll need 64-bit libmagic binaries which can be found here: https://github.com/pidydx/libmagicwin64. 
Drop the dlls in C:\Windows\System32 and python magic will import correctly.
-- Newer version can be found here: https://github.com/nscaife/file-windows.


---------------------------------------------------------------------------------------------------------------

### 2. Quickstart

The main class is  Download import it in your project as so:
```
from simple_image_download import Downloader simp 
```
Then create a new class instance
```
response = simp.simple_image_download()
```
Next you can use response to activate methods:
```
response.download(keywords, [limit])
```
 
### Downloads Images
```
from scraper import Downloader simp 
 
response = simp.simple_image_download()
response.download(‘bear supermario’, limit=5)
 
```
##### Get Only the Pictures URL and Store them in the Class cache:

```
from simple_image_download import Downloader simp 
response = simp.simple_image_download()
response.search_urls(‘bear supermario’, limit=15)
 
for url in response.cache:
    print(url)
 
```
 
---------------------------------------------------------------------------------------------------------------
 

### 3. API
 
##### *class* Downloader(extensions=None)
 
**Parameters**:
* extension -- Type of extension allowed to be downloaded, if left None defaults are:
 
 `{‘.jpg’, ‘.png’, ‘.ico’, ‘.gif’, ‘.jpeg’}`
 
-------------------------------------------------------------


#### Functions


##### search_urls(keywords, limit, verbose=False, cache=True, timer=None)
 
This functions returns and Caches URLs of Pictures based on:
 
1. Keywords for the search
2. File Extensions based on the class instance you define
3. How many picture per keyword you need with the limit parameter
 
* verbose => Output the links in the terminal in real time

* cache => if set to False, the URLs won’t be stored in the class instance, default is True

* timer => Default is set to 100_000 Looks up, defines the number of WebPages's 'chunks' will search. In the function scan_webpage a 100_000 lookkup means that it will loop up to 100_000 before stop.

Usefule in case of a picture that is not been found, so won't allow to loop indefinitely.
 
##### download(keywords, limit, verbose=False, cache=True, download_cache=False, timer=None)

This functions downloads pictures into defined class instance’s directory:
 
1. Keywords for the search
2. File Extensions based on the class instance you define
3. How many picture per keyword you need with the limit parameter
4. The directory is named after the Keyword.
5. Pictures have a unique ID, so that multiple downloads can persome
 
* verbose => Output the links in the terminal in real time

* cache => if set to False, the URLs won’t be stored in the class instance, default is True

* download_cache => allows to download all the URLs stored in the Downloader's instance Cache. Remember to clear the cache afterwards with Downloader.flush_cache

* timer => Default is set to 100_000 Looks up, defines the number of WebPages's 'chunks' will search. In the function scan_webpage a 100_000 lookkup means that it will loop up to 100_000 before stop.

Useful in case of a picture that is not been found, so won't allow to loop indefinitely.
 
##### flash_cache():
 
Clears the class instance’s cache which is stored in instance.cached_urls

-------------------------------------------------------------


#### Properties
 
##### directory
 
The directory where the Picture are saved, default is in ‘images/’.
You can set the default directory like this:
```
my_downloader = simp.simple_image_download()
my_downloader.directory = ‘my_dir/bla/’

```

##### get_dirs


Set of all sub Directories where the picture where saved .
 
#### cached_urls

 
All of the cached urls performed with the search of the function Downloader.get_urls()

Is a Dictionary with this schema:

`{'file_name': [Dir_path, URL_content]}`
 
User Downloader.flash_cache() to clear it or run my_downloader.download(download_cache=True)
to download the whole content.

---------------------------------------------------------------------------------------------------------------

