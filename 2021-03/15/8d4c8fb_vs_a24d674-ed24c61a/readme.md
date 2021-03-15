More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/270876377

Benchmark settings:

```json
{
    "id": "01cace8c-c232-482e-b31b-87f2f16250c2",
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
        "sha": "8d4c8fb637741d881d5cdc9faf167adefd93fb67",
        "build": true
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 575
    }
}
```
