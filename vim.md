Vim useful commands
====================

###Open a file with Litle-Endian encoding


	e ++enc=utf-16le filename 
    
###Show errors while starting vim (Usually with message: Press any key to continue while starting vim)


	:messages 

###YouCompleteMe configuration

After installing the plugin a configuration file should be added in the root directory where YouCompleteMe should offer to complete the code.

The name of the file should be .tern-config

The content of the file should be similar to the following:

	{
		"libs": [
			"browser"
		],
		"plugins": {
			"node": {},
			"es_modules": {},
			"commonjs": {},
			"webpack": {},
			"complete_strings": {},
			"angular": {}
		}
	}

##Usefull links

[How to record and play in Vim](http://www.thegeekstuff.com/2009/01/vi-and-vim-macro-tutorial-how-to-record-and-play/)
