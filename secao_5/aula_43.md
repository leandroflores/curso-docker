## Aula 43 - Execução do Container

**Objetivo:** criar um *container* para a **imagem Docker**.

Um dos objetivos é criar um servidor Python.

1 - Criar um diretório novo para a **imagem**.

2 - Criar um arquivo `index.html`:

```html
<p>Hello from Python!</p>
```

3 - Criar um arquivo `run.py`:
```python
import logging
import http.server
import socketserver
import getpass

class MyHTTPHandler(http.server.SimpleHTTPRequestHandler):

    def log_message(self, format: str, *args: logging.Any) -> None:
        logging.info("%s - - [%s] %s\n"% (
            self.client_address[0], 
            self.log_date_time_string(), 
            format%args
            ))

logging.basicConfig(
     filename="/log/http-server.log",
     format="%(asctime)s - %(levelname)s = %(message)s",
     level=logging.INFO
)
logging.getLogger().addHandler(logging.StreamHandler())
logging.info("start...")
PORT = 8000

httpd = socketserver.TCPServer(("", PORT), MyHTTPHandler)
logging.info(f"listen port: {PORT}")
logging.info(f"user: {getpass.getuser()}")
httpd.serve_forever()
```

Este arquivo é um servidor Python HTTP.
