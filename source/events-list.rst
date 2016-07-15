.. _events-list:

Event List
==========

webitel::domain_create
++++++++++++++++++++++

New webitel domain was created.

**Example**::

        Event-Subclass: webitel::domain_create
        Event-Name: CUSTOM
        Event-Domain: my-new-domain.webitel.com
        Domain-Name: my-new-domain.webitel.com
        variable_customer_id: 16009223091
        variable_default_language: en
        Event-UUID: 82e2403f-eeea-4181-b4b4-4d30e0146f55
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 07:59:28
        Event-Date-GMT: Fri, 15 Jul 2016 07:59:28 GMT
        Event-Date-Timestamp: 1468569568047209
        Event-Calling-File: mod_event_socket.c
        Event-Calling-Function: parse_command
        Event-Calling-Line-Number: 2256
        Event-Sequence: 332345

webitel::domain_destroy
+++++++++++++++++++++++

New webitel domain was destroyed.

**Example**::

        Event-Subclass: webitel::domain_destroy
        Event-Name: CUSTOM
        Event-Domain: my-new-domain.webitel.com
        Domain-Name: my-new-domain.webitel.com
        variable_customer_id: 16009223091
        variable_default_language: en
        Event-UUID: 9c1533f9-2c5c-4d88-9e33-6823cdbad341
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:10:41
        Event-Date-GMT: Fri, 15 Jul 2016 08:10:41 GMT
        Event-Date-Timestamp: 1468570241667207
        Event-Calling-File: mod_event_socket.c
        Event-Calling-Function: parse_command
        Event-Calling-Line-Number: 2256
        Event-Sequence: 332627

webitel::user_create
++++++++++++++++++++

New webitel user was created.

**Example**::

        Event-Subclass: webitel::user_create
        Event-Name: CUSTOM
        Event-Domain: demo.webitel.com
        Event-Account: 100
        Channel-Presence-ID: 100@demo.webitel.com
        User-ID: 100
        User-Domain: demo.webitel.com
        User-Scheme: account
        User-State: NONREG
        dial-string: {webitel_call_uuid=${create_uuid()},sip_invite_domain=demo.webitel.com}${sofia_contact(*/100@demo.webitel.com)},${verto_contact(100@demo.webitel.com)}
        jsonrpc-allowed-event-channels: demo,conference,presence
        jsonrpc-allowed-methods: verto
        jsonrpc-password: 100
        a1-hash: d42119700c161d9e0d00fb8d81d3e753
        cc-agent: true
        cc-agent-busy-delay-time: 15
        cc-agent-contact: {originate_timeout=15,presence_id=100@demo.webitel.com}{webitel_call_uuid=${create_uuid()},sip_invite_domain=demo.webitel.com}${sofia_contact(*/100@demo.webitel.com)},${verto_contact(100@demo.webitel.com)}
        cc-agent-max-no-answer: 3
        cc-agent-no-answer-delay-time: 10
        cc-agent-reject-delay-time: 15
        cc-agent-wrap-up-time: 10
        vm-password: 100
        vm-enabled: true
        webitel-extensions: 100
        variable_w_domain: demo.webitel.com
        variable_user_scheme: account
        variable_user_context: default
        variable_effective_caller_id_name: Supervisor
        variable_outbound_caller_id_name: 100
        variable_account_role: admin
        presence_id: 100@demo.webitel.com
        Event-UUID: e13aa874-e5a2-491f-be8e-21819ea3715a
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:14:12
        Event-Date-GMT: Fri, 15 Jul 2016 08:14:12 GMT
        Event-Date-Timestamp: 1468570452107223
        Event-Calling-File: mod_event_socket.c
        Event-Calling-Function: parse_command
        Event-Calling-Line-Number: 2256
        Event-Sequence: 332748

webitel::user_destroy
+++++++++++++++++++++

Webitel user was destroyed.

**Example**::

        Event-Subclass: webitel::user_destroy
        Event-Name: CUSTOM
        Event-Domain: demo.webitel.com
        Event-Account: 100
        Channel-Presence-ID: 100@demo.webitel.com
        User-ID: 100
        User-Domain: demo.webitel.com
        User-Scheme: account
        User-State: NONREG
        presence_id: 100@demo.webitel.com
        Event-UUID: fdf0d337-9e51-49b9-9d18-63301f2bfe74
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:16:43
        Event-Date-GMT: Fri, 15 Jul 2016 08:16:43 GMT
        Event-Date-Timestamp: 1468570603647203
        Event-Calling-File: mod_event_socket.c
        Event-Calling-Function: parse_command
        Event-Calling-Line-Number: 2256
        Event-Sequence: 332825

webitel::account_status
+++++++++++++++++++++++

Webitel user status was changed.

**Example**::

        Event-Subclass: webitel::account_status
        Event-Name: CUSTOM
        Event-Domain: demo.webitel.com
        Event-Account: 100
        Channel-Presence-ID: 100@demo.webitel.com
        Account-User: 100
        Account-User-State: ISBUSY
        Account-Role: ADMIN
        Account-Domain: demo.webitel.com
        Account-Scheme: account
        Account-Status: NONE
        Account-Online: false
        Account-Skills: english
        Account-Agent-State: Idle
        Account-Agent-Status: Available
        presence_id: 100@demo.webitel.com
        Event-UUID: c43d27e6-d443-49cf-b7a9-360060b77baf
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:18:45
        Event-Date-GMT: Fri, 15 Jul 2016 08:18:45 GMT
        Event-Date-Timestamp: 1468570725407244
        Event-Calling-File: mod_event_socket.c
        Event-Calling-Function: parse_command
        Event-Calling-Line-Number: 2256
        Event-Sequence: 332966