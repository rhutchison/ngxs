# Pubsub
Lets say you want to listen to events outside of your store or perhaps you want to
create a pub sub scenario where an event might not be tied to a store at all.
To do this, we can inject the `EventStream` observable and just listen in.
To make determining if the event is what we actually want to listen to, we have a 
RxJS pipeable operator called `ofEvent(NewAnimal)` we can use too!

```javascript
import { EventStream, ofEvent } from 'ngxs';

@Injectable()
export class RouteHandler {
  constructor(private eventStream: EventStream, private router: Router) {
    this.eventStream
      .pipe(ofEvent(NewAnimal))
      .subscribe((action) => alert('New Animal!'));
  }
}
```
