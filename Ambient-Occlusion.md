Pictures are louder than words:

Complete Album for comparison of some maps with and without AO: [http://www.bilderhoster.net/g/m3gld18a.html](http://www.bilderhoster.net/g/m3gld18a.html)

No Ambient Occlusion:
![without AO](http://www.bilderhoster.net/safeforgallerie/5wchcazj.jpg)
With Ambient Occlusion:
![with AO](http://www.bilderhoster.net/safeforgallerie/cs8y55xn.jpg)

### Is it fps-expensive?
No its not, unlike Tesseract, we implementated it into the current lightmap-system. 
This means your FPS do not change at all!


Even in other Branches (without this extension) and Sauerbraten Collect, your maps will still look the same (with the Ambient Occlusion Shadows). 

That is because it depends just on the calclight-process (/calclight 1).

However calclighting may take a little longer. 
