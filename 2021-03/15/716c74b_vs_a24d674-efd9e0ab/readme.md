More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/270858039

Benchmark settings:

```json
{
    "id": "c2124154-600e-4d65-ad06-be94a198ec11",
    "reference": {
        "spec": "sirius@6.5.7 +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "electronic-structure/SIRIUS",
        "sha": "a24d674330b97675090853be47ef2269f1f7185e",
        "build": true
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "electronic-structure/SIRIUS",
        "sha": "716c74b9e40f2dc514547b13861ce8c977f50e6c",
        "build": true
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 575
    }
}
```
