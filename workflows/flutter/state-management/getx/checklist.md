# GetX implementation checklist

- [ ] Confirm GetX is the selected state-management workflow and inspect nearby project conventions.
- [ ] Keep one feature responsibility per controller and preserve architecture boundaries.
- [ ] Register feature dependencies in the appropriate binding and match registration lifetime to route/app lifetime.
- [ ] Model required loading, success/empty, and failure states explicitly.
- [ ] Keep reactive rebuild regions narrow and dispose workers/subscriptions/resources.
- [ ] Use only the selected routing API; keep UI and I/O out of the controller where the architecture assigns them elsewhere.
- [ ] Cover important controller transitions and user-visible states with isolated tests.
- [ ] Report checks run and any intentional workflow deviation.
