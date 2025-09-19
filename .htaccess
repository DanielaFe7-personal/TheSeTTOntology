# Turn off MultiViews
Options -MultiViews

# Ensure correct MIME types for ontology files
AddType application/rdf+xml .rdf
AddType text/turtle .ttl
AddType application/owl+xml .owl

# Enable rewrite engine
RewriteEngine On
RewriteBase /sett
RewriteOptions Inherit

# --- Serve HTML documentation when browsers request it ---
RewriteCond %{HTTP_ACCEPT} !application/rdf\+xml.*(text/html|application/xhtml\+xml)
RewriteCond %{HTTP_ACCEPT} text/html [OR]
RewriteCond %{HTTP_ACCEPT} application/xhtml\+xml [OR]
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/.*
RewriteRule ^ontology/$ index.html [R=303]

# --- Serve HTML with anchors for classes/properties ---
RewriteCond %{HTTP_ACCEPT} !application/rdf\+xml.*(text/html|application/xhtml\+xml)
RewriteCond %{HTTP_ACCEPT} text/html [OR]
RewriteCond %{HTTP_ACCEPT} application/xhtml\+xml [OR]
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/.*
RewriteRule ^ontology/(.+) index.html#$1 [R=303,NE]

# --- Serve RDF/XML when requested ---
RewriteCond %{HTTP_ACCEPT} application/rdf\+xml
RewriteRule ^ontology/ ontology.rdf [R=303]

# --- Serve Turtle when requested ---
RewriteCond %{HTTP_ACCEPT} text/turtle
RewriteRule ^ontology/ ontology.ttl [R=303]

# --- Serve OWL/XML when requested ---
RewriteCond %{HTTP_ACCEPT} application/owl\+xml
RewriteRule ^ontology/ ontology.owl [R=303]

# --- Default: serve Turtle if nothing else matches ---
RewriteRule ^ontology/ ontology.ttl
