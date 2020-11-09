More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/213614069

Benchmark settings:

```json
{
    "id": "e61f1c18-8414-4ef0-87bd-a2cc8c74587c",
    "filter": "Au-surf|Si63Ge|SiO2-ANA-kpoint-parallel",
    "reference": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "81702c64a8be67a2936e3e8bb8ca2c9083dee03b",
        "build": false
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "4f6bf1684449bb549717c67734c215f779f51100",
        "build": false
    },
    "report_to": {
        "repository": "haampie/SIRIUS",
        "type": "pr",
        "issue": 6
    }
}
```
