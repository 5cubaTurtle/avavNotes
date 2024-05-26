#blade-ranger #logging

usage:
```python
import logging

logger = logging.getLogger("sld")
logger.setLevel(logging.DEBUG)
fh = logging.FileHandler('/home/robot/sld.log')
fh.setLevel(logging.DEBUG)
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
fh.setFormatter(formatter)
logger.addHandler(fh)

logger.warning("Cannot log all BLD: shared memory is #{} and lines is #{}".format(len(sm), len(lines)))
```
