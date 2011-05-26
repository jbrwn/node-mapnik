
# Node-Mapnik
      
  Bindings to the [Mapnik](http://mapnik.org) tile rendering library for [node](http://nodejs.org).
  
    var mapnik = require('mapnik');
    var http = require('http');
    
    var port = 8000;
    
    http.createServer(function (req, res) {
      var map = new mapnik.Map(256,256);
      map.load("./examples/stylesheet.xml");
      map.zoom_all();
      map.render(map.extent(),"png",function(err,buffer){
          if (err) {
            res.writeHead(500, {'Content-Type':'text/plain'});
            res.end(err.message);
          } else {
            res.writeHead(200, {'Content-Type':'image/png'});
            res.end(buffer);
          }
      });
    }).listen(port);
  
  For more see 'examples/'


## Development Status
  
  Prototype at this point, API will be frequently changing.
  
  Developed on OS X (10.6)
  
  Tested on Debian Squeeze, Ubuntu Maverick, and Centos 5.4.
  

## Depends

  node (development headers) >= v0.2.3
  
  mapnik 2.0 / (latest trunk >= r2898)
  
  node-pool for some examples (npm install -g generic-pool)
  
  expresso and >= node v0.4.x for tests (npm install expresso)
  
  npm >= 1.0 (if you use npm to install deps)


## Installation
  
  Install node-mapnik:
  
    $ git clone git://github.com/mapnik/node-mapnik.git
    $ cd node-mapnik
    $ ./configure
    $ make
    $ sudo make install

  For more details see 'docs/install.txt'

  Or you can also install via npm:
  
    $ npm install -g mapnik


## Quick rendering test

  To see if things are working try rendering a world map with the sample data
  
  From the source checkout root do:
  
    $ ./examples/simple/render.js ./examples/stylesheet.xml map.png

  
## Examples

  See the 'examples/' folder for more usage examples.


## Tests

  To run the expresso tests first install expresso and step.
  
     $ npm install -g expresso
     $ npm install -g step
  
  Then run:
  
    $ make test


## License

  BSD, see LICENSE.txt