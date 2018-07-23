# Robustness

Every API implementation and API consumer **MUST** follow Postel's law:

> _Be conservative in what you send, be liberal in what you accept._
>
> _–_ [_John Postel_](https://en.wikipedia.org/wiki/Robustness_principle)

That is, send the necessary minimum and be tolerant as possible while consuming another service \([tolerant reader](https://martinfowler.com/bliki/TolerantReader.html)\).

