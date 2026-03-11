# 2026-03-10 LiteLLM Connectivity

Investigated LXC `101` (`litellm`) after Aria reported the remote backend as unavailable.

## Result

LiteLLM is up and reachable.

## Verified facts

- Container `101` is running.
- `litellm.service` is active.
- LiteLLM is listening on `0.0.0.0:4000`.
- Direct authenticated request from the workstation to `http://10.10.10.10:4000/v1/models` succeeded.
- The model list includes `gemini-3.1-flash-lite-preview`.

## Important detail

The earlier `remote_backend_up=False` signal from Aria was not evidence that the LiteLLM container was down.

Likely cause:

- the health check was run from a restricted execution context that could not perform the network call, or
- an unauthenticated probe hit `/v1/models` and received `401 Unauthorized`

## Service notes

- LiteLLM runs from `/opt/litellm/config.yaml`
- service port: `4000`
- configured master key is stored on the container and not copied into this repo

## Follow-up

- If desired, verify Aria-to-LiteLLM health checks outside the restricted execution context.
- Watch LiteLLM logs for unauthenticated probes that trigger noisy `401` responses.
