# A contract without an algorithm

This illustrative Python cluster assumes the interview already settled the rules below. Adapt contracts to the real project; do not impose these domain rules on another task. The surrounding project defines `BookingRequest`, `Reservation`, `Slot`, and `Sequence`.

```python
# === START: Kevin owns available_slots ===
def available_slots(
    request: BookingRequest,
    reservations: Sequence[Reservation],
) -> list[Slot]:
    """Return the requested candidate slots that can be booked.

    request: validated request with candidate slots and a resource ID.
    reservations: validated existing reservations, possibly for other resources.
    Result: available candidates in their original order, with no added slots.

    Contract: exclude candidates overlapping a reservation for this resource.
    Intervals are half-open; touching endpoints do not overlap. Empty
    reservations return every candidate. Neither input may be mutated.
    Caller validates positive durations and consistent timezone-aware values;
    this function performs no I/O. The booking preview calls it before showing
    options, and propagates NotImplementedError as an incomplete feature.
    """
    raise NotImplementedError("Kevin owns available_slots")
# === END: Kevin owns available_slots ===
```

The comment specifies observable outcomes and caller guarantees. It deliberately leaves the implementation and choice of algorithm to Kevin. Put any second cluster in its own meaningful region rather than adding blank helper functions that dictate a solution.
