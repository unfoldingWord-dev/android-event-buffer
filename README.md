# android-event-buffer
A very simple tool for registering one-way events on objects.


##USAGE

The talker can be any class. Below is an example of a DialogFragment.

```java
public class MyTalker extends DialogFragment implements EventBuffer.OnEventTalker {
    public static final int EVENT_HELLO_WORLD = 0;
    private EventBuffer buffer = new EventBuffer();

    @Override
    public View onCreateView(LayoutInflator inflater, ViewGroup container, Bundle savedInstanceState) {
        View v;
        // do normal on-create stuff..

        this.buffer.write(this, EVENT_HELLO_WORLD, null);

        return v;
    }

    @Override
    public void onDestroy() {
        this.buffer.removeAllListeners();
        super.onDestroy();
    }

    @Override
    public EventBuffer getEventBuffer() {
        return this.buffer;
    }
}
```

The listener can be any class. Below is an example of an Activity.

> TODO: write example of listener.