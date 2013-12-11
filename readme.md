The Node.js deploy server
=========================
Node.js service is designed to help you deploy and manage your node.js web services. 
This is server part. Client part is [node-deploy-client](https://github.com/AndyGrom/node-deploy-client)

Features
--------
1. Easy installation.
2. Your services launch by dint of [forever-monitor](https://github.com/nodejitsu/forever-monitor).
3. Installing as Linux daemon or Windows service.

Usages
------------
1. Install package

   Ensure administrative rights and run command in terminal

	```bash
	npm install node-deploy-server -g
	```

2. Configuration

   Edit "nodehosting.json" file in /etc folder on linux-based OS or in root package folder on Windows:
	```javascript
	{
		"port" : 15478,						    // service port
		"username" : "admin",				    // username for client application
		"password" : "admin",				    // password for client application
        "applications" : {                      // list of your hosted applications
            "application1" : {                  // your application name
                "path" : "../applications",     // root path for deployment application
                "foreverConfig" : {             // config options for forever-monitor, if corresponding plugin is switched on
                    "cwd" : "../applications/application1"
                },
                "plugins" : [                   // extensions to process received file
                    "unpack",                   // unpack archive and ensure target folder
                    "installDependencies",      // launch command 'npm install' into root folder
                    "startProcess"              // launch your service by dint of forever-monitor (see <https://github.com/nodejitsu/forever-monitor>)
                ]
            }
        }
	}
	```

3. Run service

    * as command-line tool
	```bash
	node-server-deploy
	```

	* as windows service
	```command
	sc start nodehosting.exe
	```

	* as linux daemon
	```
	service nodehosting start
	```

Service ready. To deploy application use [node-deploy client side](https://github.com/AndyGrom/node-deploy-client)

Supported OS
------------
The software is tested on the following operating systems: CentOS 6, Fedora 18, Windows 7

License
-------
The MIT License

Copyright (c) 2013 Gromozdov Andrey Alexandrovich.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.