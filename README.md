# identifying-name-of-the-compromised-account


## Investigation

I was tasked with identifying authentication activity related to accounts with `uid=0`, which is typically associated with the root account on Linux systems. The root account has the highest level of privileges and can perform administrative operations.

To investigate this activity, I accessed the `auth.log` file, which contains authentication-related events, including session information. I used the `grep` command to search the log for entries containing `uid=0`.

### Command Used

```bash
grep "uid=0" auth.log
```

This command searches `auth.log` for lines containing the exact text `uid=0`, allowing me to identify relevant authentication records.

**Screenshot 1: Command Execution**

Insert a screenshot showing the command executed in the terminal.

![Command Execution](screenshots/command.png)

### Reviewing the Output

After executing the command, I reviewed the matching log entries to identify information relevant to the investigation. The key message I identified was:

```text
session opened for user root
```

This message explicitly identifies `root` as the account for which a session was opened.

**Screenshot 2: Command Output**

Insert a screenshot showing the relevant output returned by the command.

![Command Output]([screenshots/output.png](https://github.com/lenkamokoenaxm-arch/identifying-name-of-the-compromised-account/blob/9dd676a50b4186102141436ee70fef70d381a93b/Screenshots/name%20of%20compromised%20account.png))

## Findings

After investigating the `auth.log` file, I identified the root account in the authentication records. The key evidence was the message:

`session opened for user root`

This indicates that a session was opened for the root account. Since the root account typically has `UID 0` and administrative privileges, this finding was relevant to the investigation of privileged account activity.

The log message confirms that a session was opened for root, but it does not, by itself, prove that the account was compromised or that the session was unauthorized.

## Conclusion

I successfully identified the root account as the user associated with the session-opening event recorded in the authentication logs. By using `grep "uid=0" auth.log`, I searched for relevant entries and investigated the resulting information to support my findings.

This task demonstrated how Linux authentication logs can be examined using command-line tools to investigate privileged account activity.
