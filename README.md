The script was created based on https://sspai.com/post/38942

Instruction: 
- Open directly using a browser (I've only tested Chrome)
- Drag and drop original KML downloads from FR24
- The script will automatically process and download each file. There might be a browser prompt to ask user to enable multiple-file download on Chrome.

Notes/Caveats: 
- It works 99% of the time (I have 150+ domestic/international flights processed and uploads to FOW), though there is a small edge case the processed file would fail to upload.
* The processor now uses great-circle interpolation, so it takes the short geographic route when a flight crosses the International Date Line (IDL) between Alaska and Russia.
* The output is split into separate KML line segments at the IDL so a renderer does not connect +180 to -180 across the globe.
* The processor reads all coordinate tuples in each placemark, removes malformed points, and displays warnings for removed or skipped data.
* Altitude values in the source are currently ignored; output is a 2D ground track.
* FOW may still display a path as "broken" near the IDL if it handles multiple line segments or longitude wrapping differently from the KML. One test case was a JL3 flight from JFK to HND, for which the original unprocessed file could be uploaded to FOW.

