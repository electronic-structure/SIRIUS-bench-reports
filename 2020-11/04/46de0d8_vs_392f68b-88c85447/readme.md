More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/211639763

Benchmark settings:

```json
{
    "id": "70dcabba-d73a-4d4f-a01f-0a905e47939e",
    "reference": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "392f68b5626168134a99cd6d4a3cc40b87322cb7",
        "build": true
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "46de0d896d343d7768c9da756627e739ed0717b7",
        "build": true
    },
    "report_to": {
        "repository": "haampie/SIRIUS",
        "type": "pr",
        "issue": 5
    }
}
```
