Glossary

This glossary explains the coordination concepts used by Another.

Mail acknowledgement

A mail acknowledgement records a recipient's response or read state for a message. It does not assign responsibility for completing a task. See the [mail and concepts guide](../README.md#concepts).

Request ownership

Request ownership identifies the agent responsible for handling a request. A request follows the lifecycle `open → claimed → done`. Requests are node-local; a request cannot be assigned to a recipient on another node. See the [project concepts guide](../README.md#concepts) and [design decisions](DECISIONS.md).

Path hold

A path hold is an advisory, expiring reservation on project-relative file paths or globs. It helps agents coordinate overlapping work, but it is not a hard lock. Cross-machine conflicts are warnings rather than locks. See the [project concepts guide](../README.md#concepts) and [design decisions](DECISIONS.md).

Resource lease

A resource lease represents an agent's claim on a registered shared resource, such as a server, port, GPU, container, or job. A resource can have an owner lease and borrower leases. See the [resource registry guide](RESOURCES.md).

TTL expiry

TTL (time to live) determines how long a hold or resource lease remains active without renewal. Path holds have a TTL of 1 minute to 4 hours. Resource leases default to 30 minutes and are limited to 1 minute to 24 hours.

When resource leases expire, the resource becomes `lapsed` and remains listed; it is not automatically deleted. Cleanup is human-controlled: only a human can request reaping with explicit confirmation, and cleanup must happen on the resource's owning node. See the [resource registry guide](RESOURCES.md) and [design decisions](DECISIONS.md).
