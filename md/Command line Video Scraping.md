# Command line Video Scraping

**Space Thumbnail**

Search youtube for words from a .txt and download the thumbnail. Using youtube-dl [](http://rg3.github.io/youtube-dl/documentation.html#d1)[http://rg3.github.io/youtube-dl/documentation.html#d1](http://rg3.github.io/youtube-dl/documentation.html#d1)

**Downloads Small Video**

youtube-dl -a, --batch-file /Users/admin/Desktop/_SFPC/videoscrape/videoLog.txt --no-warnings -v webm --add-metadata --prefer-ffmpeg -f worstvideo --console-title

-i skips 404 links

**Messing Around**

*   youtube-dl -a /Users/admin/Desktop/_SFPC/videoscrape/videoLog.txt --no-warnings -v >> verbose.txt --write-description -o '%(autonumber)s %(title)s %(extractor)s'  stdout >> out.txt --skip-download

*   youtube-dl -a /Users/admin/Desktop/_SFPC/videoscrape/videoLog.txt --no-warnings -v >> verbose.txt -o '%(autonumber)s %(title)s %(extractor)s' >> out.txt --skip-download --autonumber-size 4

**Bash Script for Scraping Vids with Youtube-dl:**

[Jonathan Dahan](/ep/profile/tHuEvnWBdcR) : so we're using youtube-dl to scrape a .csv of video URLs. Works great. Now I'm working on a bash .sh script that will create a timestamped directory, go there, execute youtube-dl and make a couple folders for stuff

*   # Make dir with timestamp and go there
**   folder=$(date +%H%M%S)
*   mkdir $folder && cd $folder
**   # just in case the second changes between those two commands
*   # YTDL scrape from this .csv  
*   youtube-dl -a /Users/scottleinweber/Dropbox/SFPC/Day6_Sat_AlexHacks/AllVideos/data/allvideos_urlonly.csv -i —write-thumbnail /Users/scottleinweber/Dropbox/SFPC/Day7_Videoscrape/AllVideos/thumbs --no-warnings \
*   # this stuff isn't working super good, probably obvious fixes
*   -v >> verbose.txt  --write-description >> desc.txt -o '%(autonumber)s %(title)s %(extractor)s'  stdout >> out.txt --skip-download
*   # are lines 6 and 8 supposed to be on the same line? yeah, one long string of flags is how I'm running it right now. Supposed to get thumbnails, dump into folder, get titles, dump into file
**   # to show multi-line commands, append a \ at the end of each line you want to continue (ah got it)
**   # ok, so the main problem is you are trying to run the output from one command to multiple files
*   # each command just connects to 1 stdin, 1 stdout, and 1 stderr for input/output/error
*   # those options for youtube-dl, if you choose them all, will output everything
*   # then you have to parse that file to do the things you want
*   # hmm can you || or >> them out in one line?
*   # so it should look something like
*   # oh wow, gist is way better here, good call on the \operator

*

[](https://gist.github.com/jedahan/11376532)https://gist.github.com/jedahan/11376532

So then if you want to split out the information, you have to parse that file with some other utilities.

Cool, let me mess around and I'll report back. Thanks [Jonathan Dahan](/ep/profile/tHuEvnWBdcR) 

Yup, gonna go to lunch now but i'll be back here and on slack - Primo