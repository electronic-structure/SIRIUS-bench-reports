More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/204143945

Benchmark settings:

```json
{
    "id": "0f71b6c1-e2ad-4273-b5fb-3fec3c037488",
    "reference": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "a923c3c8853d846138a8b9a9c096494004b8d208",
        "build": false
    },
    "current": {
        "spec": "sirius@develop",
        "cmd": [
            "sirius.scf",
            "--iterative_solver.early_restart=0.5"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "adff978c05fe0b8ea67eae5f2174d5616f15acab",
        "build": false
    },
    "report_to": {
        "repository": "haampie/SIRIUS",
        "type": "pr",
        "issue": 4
    }
}
```
