More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/215256452

Benchmark settings:

```json
{
    "id": "31fbc3e3-5eef-4974-a61d-0ba592a569f3",
    "reference": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "0c261670dec9b96a58dd74a9134f19b00042d6d1",
        "build": true
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "8465163e5150bf9c73ec5dac4bf03576202704b3",
        "build": true
    },
    "report_to": {
        "repository": "haampie/SIRIUS",
        "type": "pr",
        "issue": 7
    }
}
```
