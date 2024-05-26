Data validation and settings management using python type annotations.
[Arjan vid](https://youtu.be/Vj-iU-8_xLs)
pydantic has extensive support for data validation, conversion and sanitizing.

example:
```python
import pydantic
from typing import Optional

class Book(pydantic.BaseModel):
	title: str
	author: str
	publisher: str
	price: float
	isbn_10: Optional[str]
	isbn_13: Optional[str]
	subtitle: Optional[str]
```