# Testing

## EC2 Stop/Start Experiment

The instance's state and networking properties were recorded before and after stopping the EC2 instance.

### Before Stop

| Property | Result |
|---|---|
| Instance state | Running |
| Public IPv4 | `<REDACTED>` |
| Private IPv4 | `<REDACTED>` |
| EBS root volume | Present |
| Nginx | Running |

### After Stop

| Property | Result |
|---|---|
| Instance state | Stopped |
| Public IPv4 | Released |
| EBS root volume | Present |

### After Start

| Property | Result |
|---|---|
| Instance state | Running |
| Public IPv4 | `<REDACTED>` |
| EBS root volume | Present |
| Nginx | Site can't be reached |

## Observations

- Stopping the instance stopped the EC2 compute resources.
- The root EBS volume persisted.
- The automatically assigned public IPv4 address was checked before and after the stop/start operation.
- Nginx availability was tested after the instance was started again.