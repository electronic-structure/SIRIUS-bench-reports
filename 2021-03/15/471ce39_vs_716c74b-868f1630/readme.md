More logs available here: https://gitlab.com/cscs-ci/electronic-structure/benchmarking/-/pipelines/270857107

Benchmark settings:

```json
{
    "id": "f142e99a-3a8a-4156-9c89-5272715b5472",
    "reference": {
        "spec": "sirius@6.5.7 +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "716c74b9e40f2dc514547b13861ce8c977f50e6c",
        "build": true
    },
    "current": {
        "spec": "sirius@develop +scalapack",
        "cmd": [
            "sirius.scf"
        ],
        "repo": "haampie/SIRIUS",
        "sha": "471ce3923998c3650c74d3ce76dc59fb7a72b348",
        "build": true
    },
    "report_to": {
        "repository": "haampie/SIRIUS",
        "type": "pr",
        "issue": 12
    }
}
```
