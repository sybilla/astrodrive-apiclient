# astrodrive-apiclient
JavaScript library for AstroDrive API

# installation

  npm install astrodrive-apiclient

# usage

```TypeScript
import { HttpClient } from 'aurelia-fetch-client';
import {AstroDriveApiClientV1_0} from 'astrodrive-apiclient';

export class App {
  httpclient: HttpClient;
  client: AstroDriveApiClientV1_0;

  constructor() {
      this.httpclient = new HttpClient().configure(config => {
        config
          .withInterceptor({
              request(request: Request) {
                  request.headers.append('Authorization', 'Bearer ' + 'mock');
                  return request;
              }
          });
      });
      this.client = new AstroDriveApiClientV1_0('http://localhost:5001', this.httpclient);
      this.client.apiDirectoryList().then(result => {
        this.message = result.id;
    });
}

  public message: string = '';
}
```
