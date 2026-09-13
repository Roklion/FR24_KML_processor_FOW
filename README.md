The script was created based on https://sspai.com/post/38942

Instruction: 
- Open directly using a browser (I've only tested Chrome)
- Drag and drop original KML downloads from FR24
- The script will automatically process and download each file. There might be a browser prompt to ask user to enable multiple-file download on Chrome.

Features and benefits:
- Easy to use: open the standalone HTML file in a native browser and drag and drop KML files onto it.
- Fixes disconnected or overly sparse flight paths by adding points at approximately 1 km intervals between recorded positions.
- Handles paths crossing the International Date Line without creating a line across the globe by splitting the output into separate KML line segments.
- Reduces the information load for Fog of World (FOW) and FOW Eraser by converting verbose FR24 placemarks, descriptions, styles, folders, timestamps, and altitude data into a lightweight 2D path.
- Processes multiple FR24 files in one batch and reports malformed or skipped points without stopping the rest of the batch.

Notes/Caveats: 
- The processor assumes consecutive valid points belong to the same flight path. If the source contains a genuinely disconnected or very large gap, it will still treat the points as connected and insert approximately one point per kilometer along the great-circle route between them.
* The processor now uses great-circle interpolation, so it takes the short geographic route when a flight crosses the International Date Line (IDL) between Alaska and Russia.
* The output is split into separate KML line segments at the IDL so a renderer does not connect +180 to -180 across the globe.
* The processor reads all coordinate tuples in each placemark, removes malformed points, and displays warnings for removed or skipped data.
* Altitude values in the source are currently ignored; output is a 2D ground track.
* FOW may still display a path as "broken" near the IDL if it handles multiple line segments or longitude wrapping differently from the KML. One test case was a JL3 flight from JFK to HND, for which the original unprocessed file could be uploaded to FOW.

