More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/216597901

Benchmark settings:

```json
{
    "id": "6d3bff7b-4db1-43a6-b7e6-83eb3fc823d4",
    "reference": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "electronic-structure/SIRIUS",
        "sha": "16c96c9521ba11c164891eb65cdeac5a4e0e34b3",
        "build": true
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf",
            "--mixer.type=broyden2"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "0308c074b92841e183b2aa72e055c15d8e0ec6ab",
        "build": true
    },
    "report_to": {
        "repository": "electronic-structure/SIRIUS",
        "type": "pr",
        "issue": 586
    }
}
```
