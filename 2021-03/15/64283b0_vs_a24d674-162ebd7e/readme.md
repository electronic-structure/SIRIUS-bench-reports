More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/270894041

Benchmark settings:

```json
{
    "id": "511944c9-5b86-495e-b341-d82d94cd821b",
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
        "sha": "64283b0bdde21ce92493e897e38c4105358cbbe3",
        "build": true
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 575
    }
}
```
