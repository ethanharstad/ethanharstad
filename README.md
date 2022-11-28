```python
from dataclasses import dataclass
from typing import Tuple

class Meta(type):
    def __new__(cls, name, bases, attrs):
        new_cls = super().__new__(cls, name, bases, attrs)
        return dataclass(unsafe_hash=True, frozen=True)(new_cls)

class Bio(metaclass=Meta):
    name        : str = "Ethan Harstad"
    designation : str = "Cloud Engineer"
    company     : str = "Ocelot Consulting"
    hometown    : str = "Des Moines, IA"
    website     : str = "https://harstad.co"

class Stack(metaclass=Meta):
    languages       : Tuple[str, ...] = ("Python", "Typescript", "Rust", "Dart", "Go")
    platforms       : Tuple[str, ...] = ("Terraform", "Kubernetes", "Flutter")
    cloud_providers : Tuple[str, ...] = ("AWS", "Azure", "GCP", "DigitalOcean", "CloudFlare")

class Social(metaclass=Meta):
    linkedin : str = "https://www.linkedin.com/in/ethanharstad/"
    github   : str = "https://github.com/ethanharstad"
```