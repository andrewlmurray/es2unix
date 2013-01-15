# es2unix

Elasticsearch API consumable by the command line.

JSON is wonderful for services, but not always for humans.  The
tabular format is compact.  es2unix strives to keep spaces significant
so all output works with existing line-oriented *NIX tools.


# Install

es2unix's only dependency is Java (Oracle or OpenJDK).  Version 7
should be preferred, but there is no functional difference with 6.
Earlier versions aren't supported.

        curl -s download.elasticsearch.org/es2unix/es >~/bin/es
        chmod +x ~/bin/es

# Usage

The `es` command takes subcommands and a few options.  It assumes it's
talking to ES at its default HTTP port using `http://localhost:9200`
but accepts `-u` to change that.  It must be a fully qualifed URL with
scheme, host, & port.

You can also supply `-v`, for most commands, to print a column header.


## Version

        % es version
        es            1.0.0       
        elasticsearch 0.21.0.Beta1


## Health

        % es health
        kluster green 4 3 6 17 0 0 0


## Master

        % es master
        J-erllamTOiW5WoGVUd04A 127.0.0.1 Slade, Frederick

## Nodes

        % es nodes
        Uv1Iy8FvR0y6_RzPXKBolg 127.0.0.1 9201 127.0.0.1 9300   d Cannonball I          
        J-erllamTOiW5WoGVUd04A 127.0.0.1 9200 127.0.0.1 9301 * d Slade, Frederick      
        j27iagsmQQaeIpl6yU6mCg 127.0.0.1 9203 127.0.0.1 9303 - c Georgianna Castleberry
        T1aFDU2BSUm748gYxjEN9w 127.0.0.1 9202 127.0.0.1 9302   d Living Tribunal       


## Shards

        % es shards -v
        index  shard pri/rep state   size    size-bytes  docs ip        node            
        wiki       1 r       STARTED 404.2mb  423845459 28576 127.0.0.1 Cannonball I    
        wiki       0 p       STARTED 404.8mb  424543961 28826 127.0.0.1 Cannonball I    
        wiki       2 p       STARTED 406.9mb  426734771 28718 127.0.0.1 Cannonball I    
        _river     0 p       STARTED 79b             79     0 127.0.0.1 Cannonball I    
        wiki       3 p       STARTED 409.1mb  429013649 28761 127.0.0.1 Cannonball I    
        wiki       4 p       STARTED 410.6mb  430608757 28819 127.0.0.1 Cannonball I    
        wiki       0 r       STARTED 404.8mb  424543961 28826 127.0.0.1 Slade, Frederick
        wiki       2 r       STARTED 406.9mb  426738791 28718 127.0.0.1 Slade, Frederick
        wiki       3 r       STARTED 409.1mb  429017254 28761 127.0.0.1 Slade, Frederick
        _river     0 r       STARTED 79b             79     0 127.0.0.1 Slade, Frederick
        wiki       4 r       STARTED 410.6mb  430611290 28819 127.0.0.1 Slade, Frederick
        wiki       0 r       STARTED 404.8mb  424543961 28826 127.0.0.1 Living Tribunal 
        wiki       1 p       STARTED 404.2mb  423851451 28576 127.0.0.1 Slade, Frederick
        wiki       1 r       STARTED 404.2mb  423845459 28576 127.0.0.1 Living Tribunal 
        wiki       2 r       STARTED 406.9mb  426734751 28718 127.0.0.1 Living Tribunal 
        wiki       3 r       STARTED 409.1mb  429013629 28761 127.0.0.1 Living Tribunal 
        wiki       4 r       STARTED 410.6mb  430608737 28819 127.0.0.1 Living Tribunal 

# Contributing

es2unix is written in Clojure.  You'll need leiningen 2.0+ to build.

        % make package

# License

        This software is licensed under the Apache 2 license, quoted below.
        
        Copyright 2009-2012 Shay Banon and ElasticSearch <http://www.elasticsearch.org>
        
        Licensed under the Apache License, Version 2.0 (the "License"); you may not
        use this file except in compliance with the License. You may obtain a copy of
        the License at
        
            http://www.apache.org/licenses/LICENSE-2.0
            
        Unless required by applicable law or agreed to in writing, software
        distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
        WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
        License for the specific language governing permissions and limitations under
        the License.
