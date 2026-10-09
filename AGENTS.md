# Enemy asset workflow

The user requests that every enemy asset produced for this repository be uploaded
to this GitHub repository, mimisen0512-sys/enemy_yama, after creation and validation.
Store each character in assets/enemies/<asset_id>/ with its six transparent PNG
parts, assembled preview, parts overview, placement metadata, and validation notes.
Commit the completed assets and push using the existing platform authentication.
Preserve unrelated changes. Never force-push. If upload fails, report the actual
failure without claiming that GitHub contains the assets.
Provide a GitHub link to the original assembled preview after successful upload.
Do not replace the original preview with a newly generated display approximation.

The latest visual requirement is a flat design with weak outlines. The assembled
enemy silhouette itself must be wider than tall, not only placed on a landscape
canvas. Use a transparent 1536x1024 canvas and measure actual alpha bounds after
assembly. Preserve the six-part structure and pupil-free eyes. Do not achieve
the wide silhouette by nonuniformly stretching the artwork.
