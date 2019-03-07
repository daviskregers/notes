# IPTables

## Sources:
- [https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/](https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/)

IPTables uses three different chains: `input`, `forward` and `output`.

### `Input` 
This chain is used to control the begaviour for incomming connections. 
For example, if a user attempts to ssh into the system, iptables will attempt to match the IP address and port to a rule in the input chain.

### `Forward` 
This chain is used for incoming connections that aren't actually being delivered locally. 
Think of a router - data is always being sent to it but rarely actually destined for the router itself, it is forwarded instead.

To check whether the system uses / needs the forward chain:

```bash
iptables -L -V
```

### `Output`

This chain is used for outgoing connections. For example, if you try to ping a website, iptables will check it's output chain 
to see what the rules are regarding ping and the domain before making a decision to allow or deny the connection attempt.

## Policy chain default behaviour

Before going in and configuring specific rules, you'll want to decide what you want the default behaviour of the three chains
to be. 

To see what you policy chains are currently configured to do with unmatched traffic:

```bash
iptables -L
```

More times than not, you'll want your system to accept connections by default. 
Unless you've changed the policy chain rules previously, this setting should already be configured.
Either way, you can do that by using these commands:

```bash
iptables --policy INPUT ACCEPT
iptables --policy OUTPUT ACCEPT
iptables --policy FORWARD ACCEPT
```

By defaulting to the accept rule, you can then use iptables to deny specific IP addresses or ports, while accepting all other
connections. 

If you rather deny all connections and manually specify which ones you want to allow to connect, you should change
the default policy of your chains to drop. Doing this would probably only be useful for servers that contain sensitive information
and only ever have the same IP addresses connecting to them.

```bash
iptables --policy INPUT DROP
iptables --policy OUTPUT DROP
iptables --policy FORWARD DROP
```

## Connection-specific responses

With your default chain policies configured, you can start adding rules to iptables so it knows what to do when it encounters
a connection from or to a particular IP address or port. 

The 3 most basic and commonly used responses are:

- `Accept` - allow the connection
- `Drop` - drop the connection, act like it never happened. This is the best if you don't want the source to realize your system exists.
- `Reject` - Don't allow the connection, but send back an error. This is best if you don't want a source to connect to your system and want to let them know that.

## Allowing or blocking specific connections

If you need to insert a rule above another you can use:

### Connections from a single IP address

```
iptables -A INPUT -s 10.10.10.10 -j DROP
```

### Connections from a range of IP addresses

```bash
iptables -A INPUT -s 10.10.10.0/24 -j DROP
```

or

```bash
iptables -A INPUT -s 10.10.10.0/255.255.255.0 -j DROP
```

### Connections to a specific port

```bash
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -j DROP
```

## Connection states

Many protocols like SSH require communication in both directions. For example, if you want to allow ssh connections to your system,
the input and output chains are going to need a rule added to them. 

Because of this, connection states are introducted, which gives you capability to allow two way communication but only allow one way connections 
to be established.

In this example, ssh connections from 10.10.10.10 are permitted, and it is permitted to send back information to it, 
as long as the session has already been established. 

```bash
iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 222 -d 10.10.10.10 -m state --state ESTABLISHED -j accept
```

## Saving changes

The changes that you make to your iptables rules will be scrapped the next time that the iptables service gets restarted unless
you execute a command to save the changes. This command can differ depending on your distribution:

`Ubuntu`:

```bash
sudo /sbin/iptables-save
``

`Red Hat / CentOS`

```bash
/sbin/service iptables save
```

Or

```bash
/etc/init.d/iptables save
```

## Other commands

List the currently configured iptables rules:

```bash
iptables -L
```

Adding the `-v` option will give you packet and byte information, and adding `-n` will list everything numerically. 
Hostnames, protocols and networks are listed as numbers.

To clear all the currently configured rules, you can issue the flush command

```bash
iptables -F
```
