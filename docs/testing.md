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

## EC2 Stop/Start Test

### Objective

Verify what happens to the EC2 server and its resources after stopping and starting the instance.

### Test Results

| Test | Result |
|---|---|
| Public IPv4 address changed | Yes |
| EBS volume persisted | Yes |
| Nginx automatically started | Yes |
| Nginx listening on port 80 | Yes |
| Local HTTP request | 200 OK |
| External HTTP request | 200 OK |
| Website accessible from browser | Yes |

### Troubleshooting

After the instance was started again, the website initially appeared unreachable from the browser.

I verified the server layer first:

```bash
sudo systemctl status nginx
sudo ss -lntp | grep :80
curl -I http://localhost