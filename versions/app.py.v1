
import os, time, json
import socket

from redis import Redis
from flask import Flask, request, Response, stream_with_context, jsonify

app = Flask(__name__)
db = Redis( host = os.getenv( 'REDIS', 'redis'),
            port = int(os.getenv( 'REDIS_PORT', '6379' ) )

@app.route('/')
def hello():
    db.incr('count')

    host = socket.gethostname()
    return '''[%s] Redis counter value=%s\n''' % (host, db.get('count'))
    
if __name__ == "__main__":
    app.run(host="0.0.0.0", debug=True)
