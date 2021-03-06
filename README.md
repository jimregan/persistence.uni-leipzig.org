persistence.uni-leipzig.de
==========================

All ontologies used in NIF (nif-core + vocabulary modules )

## Workflow for the ontologies

### '\#' vs. '/' URIs
There has been an ongoing debate about '\#' vs. '/' . We focus on ontologies with '\#' here with URIs like:
http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core\#String 
Note that ontologies with '/' URIs need to published differently (partly discussed here: http://lists.w3.org/Archives/Public/semantic-web/2013Apr/0157.html). 

### Workflow for '\#' ontologies
1. I edit the ontologies in turtle syntax with the Geany text editor or any other Turtle editor e.g. http://aksw.org/Projects/Xturtle.html ),
   This allows me to make developers comments using "#" directly in the source, see e.g. nlp2rdf/ontologies/nif-core.ttl
2. When I am finished I use rapper (http://librdf.org/raptor/rapper.html) to convert it to rdfxml ( nlp2rdf/ontologies/nif-core.owl )
3. I am versioning the ontologies in a folder with the version number, e.g. version-1.0
   If somebody wants to find old ontologies, she can find them in the GitHub repository, which is linked from the ontology.
   I assume this is not often required, but it is nice to keep old versions.
   The old versions should be linked to in the comment of the ontology, see the header of nif-core.ttl
4. Then I use git push to push the changes to our server
5. (not yet) I use a simple OWL2HTML generator, e.g. https://github.com/specgen/specgen
6. add yourself to http://prefix.cc, see e.g. http://prefix.cc/nif
7. The versions are switched and published by these .htaccess rules, e.g. <br>
<code>RewriteRule \.(owl|rdf|html|ttl|nt|txt|md)$ - [L]<br>	
	\# (in progress) RewriteCond %{HTTP_ACCEPT} text/html<br>
	\# (in progress) RewriteRule ^nif-core$ /nlp2rdf/ontologies/nif-core/version-1.0/nif-core.html [R=303,L]<br>	
	RewriteCond %{HTTP_ACCEPT} application/rdf\+xml<br>
	RewriteRule ^nif-core$ /nlp2rdf/ontologies/nif-core/version-1.0/nif-core.owl [R=303,L]<br>	
	RewriteRule ^nif-core$ /nlp2rdf/ontologies/nif-core/version-1.0/nif-core.ttl [R=303,L]<br></code>

