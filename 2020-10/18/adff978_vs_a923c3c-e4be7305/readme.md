More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/204151066

Benchmark settings:

```json
{
    "id": "f185c039-83a8-4d1c-9948-98cf6fd0e698",
    "reference": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "electronic-structure/SIRIUS",
        "sha": "a923c3c8853d846138a8b9a9c096494004b8d208",
        "build": true
    },
    "current": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "adff978c05fe0b8ea67eae5f2174d5616f15acab",
        "build": true
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 576
    }
}
```
