# Changelog
## 2.3.3 [2022-10-09]
### Changes:
* Added release year to zip file names. ([Issue #31](https://github.com/MichaelYochpaz/iSubRip/issues/31))
* If the generated path for a zip file is already taken, a number will be appended at the end of the file's name to avoid overwriting. ([Issue #34](https://github.com/MichaelYochpaz/iSubRip/issues/34))
### Bug Fixes:
* Fixed an exception being thrown if the path to downloads folder on the config is invalid.
* Fixed AppleTV URLs without a movie title not working. ([Issue #29](https://github.com/MichaelYochpaz/iSubRip/issues/29))
* Fixed issues for movies with specific characters (`/`, `:`), and Windows reserved names in their title. ([Issue #30](https://github.com/MichaelYochpaz/iSubRip/issues/30))
---
## 2.3.2 [2022-08-06]
### Changes:
* Changed config paths to the following locations:  
Windows: `%USERPROFILE%\.isubrip\config.json`  
Linux / macOS: `$HOME/.isubrip/config.json`  
More info under Notes (and examples on the [README](https://github.com/MichaelYochpaz/iSubRip#configuration) file).

### Bug Fixes:
* Fixed an error with AppleTV links for movies released before 1970 (Epoch time). ([Issue #21](https://github.com/MichaelYochpaz/iSubRip/issues/21))
* Fixed config file not being loaded on macOS. ([Issue #22](https://github.com/MichaelYochpaz/iSubRip/issues/22))
* Fixed AppleTV scraping from the same storefront. ([Issue #24](https://github.com/MichaelYochpaz/iSubRip/issues/24))

### Notes:
* Running iSubRip with a config file in the previous locations will still work, but support for them will be dropped in the future.  
* `xdg` package is no longer required or used.
---
## 2.3.1 [2022-07-15]
### Changes:
* Improved AppleTV scraping to utilize AppleTV's API instead of scraping HTML.

### Bug Fixes:
* Fixed HTML escaped (for non-English) characters not matching AppleTV's URL RegEx. ([Issue #15](https://github.com/MichaelYochpaz/iSubRip/issues/15))
---
## 2.3.0 [2022-06-23]
### Added:
* AppleTV movie URLs are now supported.
* Added a `merge-playlists` config option to treat multiple playlists that can be found on AppleTV pages as one (more info on the example config).

### Changes:
* Improved subtitles parser to perserve additional WebVTT data.
* The config value `user-agent` under `scraping` is now separated to 2 different values: `itunes-user-agent`, and `appletv-user-agent`.

### Bug Fixes:
* Fixed movie titles with invalid Windows file-name characters (example: '?') causing a crash. ([Issue #14](https://github.com/MichaelYochpaz/iSubRip/issues/14))
* Fixed iTunes store URLs without a movie title not working. ([Issue #13](https://github.com/MichaelYochpaz/iSubRip/issues/13))
---
## 2.2.0 [2022-04-25]
### Added:
* Replaced FFmpeg usage for parsing with a native subtitles parser (downloads are much faster now).
* Added a `remove-duplicates` configuration remove duplicate paragraphs. (Was previously automatically fixed by FFmpeg.)
* Added `fix-rtl` and `rtl-languages` configuration to fix RTL in RTL-languaged subtitles (has to be enabled in the config).

### Changes:
* FFmpeg is no longer required or used, and all FFmpeg-related settings are deprecated.

### Notes:
* `fix-rtl` is off by default and has to be enabled on the config. Check the `config.toml` example file for more info.
* Minimum supported Python version bumped to 3.7.
---
## 2.1.2 [2022-04-03]
### Bug Fixes:
* Fixed subtitles being downloaded twice, which causes long (doubled) download times.
---
## 2.1.1 [2022-03-28]
### Bug Fixes:
* Fixed a compatibility issue with Python versions that are lower than 3.10.
* Fixed downloading subtitles to an archive file not working properly.
* Fixed a bug where the code continues to run if subtitles download failed, as if the download was successful.
---
## 2.1.0 [2022-03-19]
### Added:
* A note will be printed if a newer version is available on PyPI (can be disabled on the config).
* Config will now be checked for errors before running.

### Changes:
* Big improvements to scraping, which is now far more reliable.
* Added release year to subtitles file names.
* Config structure slightly changed.

### Notes:
* If you use a user-config, it might need to be updated to match the new config structure.
  Example of an updated valid structure can be found [here](https://github.com/MichaelYochpaz/iSubRip/blob/main/config.toml).
---
## 2.0.0 [2022-01-30]
The script is now a Python package that can be installed using pip.

### Added:
* Added a config file for changing configurations. (Example can be found [here](https://github.com/MichaelYochpaz/iSubRip/blob/main/config.toml))
* Added an option to choose subtitles format (vtt / srt).
* Added an option to choose whether to zip subtitles files or not.
* Multiple links can be passed for downloading subtitles for multiple movies one after another.
* Temporary files are automatically removed if the script stops unexpectedly.

### Changes:
* A complete code overhaul from a single python script file to a package, while utilizing OOP and classes.
* Improved scraping algorithm for faster playlist scraping.
* FFmpeg will now automatically overwrite existing subtitles with the same file name.

### Bug Fixes:
* Fixed a bug where in some cases, no subtitles were found since the title has HTML escaped characters, which causes bad matching when checking if a valid playlist was found.
---
## 1.0.6 [2021-07-23]
### Bug Fixes:
* Fixed an issue where in some cases subtitles won't download when using `DOWNLOAD_FILTER` because of letter casing not matching.
* Fixed and improved error handling, and added more descriptive error messages. ([Issue #9](https://github.com/MichaelYochpaz/iSubRip/issues/9))
---
## 1.0.5 [2021-05-27]
### Bug Fixes:
* Fixed subtitles for some movies not being found after previous release. ([Issue #8](https://github.com/MichaelYochpaz/iSubRip/issues/8))
---
## 1.0.4 [2021-05-25]
### Bug Fixes:
* Fixed the script not working after iTunes webpage data orientation slightly changed. ([Issue #6](https://github.com/MichaelYochpaz/iSubRip/issues/6) , [Issue #7](https://github.com/MichaelYochpaz/iSubRip/issues/7))
---
## 1.0.3 [2021-04-30]
### Bug Fixes:
* Fixed a bug where subtitles for suggested movies are being downloaded if movie's main playlist is not found. ([Issue #2](https://github.com/MichaelYochpaz/iSubRip/issues/2))
* Added a "cc" tag to closed-caption subtitles' filename to avoid a collision with non-cc subtitles. ([Issue #3](https://github.com/MichaelYochpaz/iSubRip/issues/3))
---
## 1.0.2 [2021-04-15]
### Added:
* Added a User-Agent for sessions to avoid being blocked.

### Changes:
* `DOWNLOAD_FILTER` is no longer case-sensitive.
* Added `lxml` to `requirements.txt`. ([Issue #1](https://github.com/MichaelYochpaz/iSubRip/issues/1))

### Bug Fixes:
* Fixed the script not working after iTunes webpage data orientation slightly changed. ([Issue #1](https://github.com/MichaelYochpaz/iSubRip/issues/1))
---
## 1.0.1 [2020-12-13]
### Changes:
* Improved error handling.
  
### Bug Fixes:
* Fixed file name formatting.
---
## 1.0.0 [2020-11-02]
* Initial release.