from pathlib import Path
import hashlib,json
root=Path(__file__).resolve().parents[1]
manifest=json.loads((root/'docs/source_manifest.json').read_text())
for entry in manifest['files']:
    p=root/entry['path']
    assert p.is_file(),f"Missing: {p}"
    assert hashlib.sha256(p.read_bytes()).hexdigest()==entry['sha256'],f"Changed: {p}"
print(f"PASS: {len(manifest['files'])} imported files match their original bytes.")
