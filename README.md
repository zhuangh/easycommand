easycommand
===========
import os, time
import shutil 

path_to_watch = '.'
before = dict( [ (f, None ) for f in os.listdir (path_to_watch) ] )
dest_folder = '~/backups/'

iter = 0;
while 1:
    time.sleep(4)
    after = dict( [ (f, None ) for f in os.listdir (path_to_watch) ] )
    added = [ f for f in after if not f in before]
    removed = [f for f in before if not f in after ]
    if added: 
	    print "Added: ", ",".join (added)
	    dest_file = dest_folder+ added[0] + str(iter);
	    iter = iter +1;
	    shutil.move( added[0], dest_file)
	    
    if removed: 
	     print "Removed: ", ",".join (removed)

    before = after 
