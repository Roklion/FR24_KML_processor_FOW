The script was created based on https://sspai.com/post/38942

Instruction: 
- Open directly using a browser (I've only tested Chrome)
- Drag and drop original KML downloads from FR24
- The script will automatically process and download each file. There might be a browser prompt to ask user to enable multiple-file download on Chrome.

Notes/Caveats: 
- It works 99% of the time (I have 150+ domestic/international flights processed and uploads to FOW), though there is a small edge case the processed file would fail to upload.
* This involes the flight path passing Internatonal Date Line (IDL) between Alaska and Russia, where an artificial "horizontal" line was added to circling around the global.
* Most flights passing IDL are not impacted, only a few. One test case I had was a JL3 flight from JFK to HND, in which case I was able to upload the original unprocessed file to FOW.
- Also for flights crossing IDL, even after processing, the flight path might still be "broken" near the IDL. I think it has something to do with how FOW is handling/wrapping around the IDL, adding arithmatic average of the cooridinates simply doesn't work.  

