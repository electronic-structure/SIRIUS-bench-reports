More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/203586901

Benchmark settings:

```json
{
    "id": "a0b8b580-79da-4da7-bc2c-936e36a1aa1b",
    "reference": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "electronic-structure/SIRIUS",
        "sha": "a923c3c8853d846138a8b9a9c096494004b8d208",
        "build": false
    },
    "current": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf",
            "--iterative_solver.early_restart=0.3"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "adff978c05fe0b8ea67eae5f2174d5616f15acab",
        "build": false
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 576
    }
}
```
