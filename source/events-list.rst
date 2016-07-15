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

DTMF
++++

::

        Event-Name: DTMF
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:30:33
        Event-Date-GMT: Fri, 15 Jul 2016 08:30:33 GMT
        Event-Date-Timestamp: 1468571433087217
        Event-Calling-File: switch_channel.c
        Event-Calling-Function: switch_channel_dequeue_dtmf
        Event-Calling-Line-Number: 660
        Event-Sequence: 333420
        Channel-State: CS_EXCHANGE_MEDIA
        Channel-Call-State: ACTIVE
        Channel-State-Number: 5
        Channel-Name: sofia/internal/100@10.10.10.101:5064
        Unique-ID: f40305c9-1b0f-4337-8fa1-01ca62a46293
        Call-Direction: outbound
        Presence-Call-Direction: outbound
        Channel-HIT-Dialplan: false
        Channel-Presence-ID: 100@demo.webitel.com
        Channel-Call-UUID: 5e6659b8-8324-4f9d-b6ed-e7ef06057d07
        Answer-State: answered
        Channel-Read-Codec-Name: G722
        Channel-Read-Codec-Rate: 16000
        Channel-Read-Codec-Bit-Rate: 64000
        Channel-Write-Codec-Name: G722
        Channel-Write-Codec-Rate: 16000
        Channel-Write-Codec-Bit-Rate: 64000
        Caller-Direction: outbound
        Caller-Logical-Direction: outbound
        Caller-Username: 9999
        Caller-Dialplan: XML
        Caller-Caller-ID-Name: 9999
        Caller-Caller-ID-Number: 9999
        Caller-Orig-Caller-ID-Name: Igor
        Caller-Orig-Caller-ID-Number: 9999
        Caller-Callee-ID-Name: Outbound Call
        Caller-Callee-ID-Number: 100
        Caller-Network-Addr: 10.10.10.101
        Caller-ANI: 9999
        Caller-Destination-Number: 100
        Caller-Unique-ID: f40305c9-1b0f-4337-8fa1-01ca62a46293
        Caller-Source: mod_sofia
        Caller-Context: default
        Caller-Channel-Name: sofia/internal/100@10.10.10.101:5064
        Caller-Profile-Index: 1
        Caller-Profile-Created-Time: 1468571424767200
        Caller-Channel-Created-Time: 1468571424767200
        Caller-Channel-Answered-Time: 1468571430007188
        Caller-Channel-Progress-Time: 1468571424947185
        Caller-Channel-Progress-Media-Time: 0
        Caller-Channel-Hangup-Time: 0
        Caller-Channel-Transfer-Time: 0
        Caller-Channel-Resurrect-Time: 0
        Caller-Channel-Bridged-Time: 1468571430007188
        Caller-Channel-Last-Hold: 0
        Caller-Channel-Hold-Accum: 0
        Caller-Screen-Bit: true
        Caller-Privacy-Hide-Name: false
        Caller-Privacy-Hide-Number: false
        Other-Type: originator
        Other-Leg-Direction: inbound
        Other-Leg-Logical-Direction: inbound
        Other-Leg-Username: 9999
        Other-Leg-Dialplan: XML
        Other-Leg-Caller-ID-Name: Igor
        Other-Leg-Caller-ID-Number: 9999
        Other-Leg-Orig-Caller-ID-Name: Igor
        Other-Leg-Orig-Caller-ID-Number: 9999
        Other-Leg-Callee-ID-Name: Outbound Call
        Other-Leg-Callee-ID-Number: 100
        Other-Leg-Network-Addr: 10.10.10.107
        Other-Leg-ANI: 9999
        Other-Leg-Destination-Number: 100
        Other-Leg-Unique-ID: 5e6659b8-8324-4f9d-b6ed-e7ef06057d07
        Other-Leg-Source: mod_sofia
        Other-Leg-Context: default
        Other-Leg-Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Other-Leg-Profile-Created-Time: 0
        Other-Leg-Channel-Created-Time: 0
        Other-Leg-Channel-Answered-Time: 0
        Other-Leg-Channel-Progress-Time: 0
        Other-Leg-Channel-Progress-Media-Time: 0
        Other-Leg-Channel-Hangup-Time: 0
        Other-Leg-Channel-Transfer-Time: 0
        Other-Leg-Channel-Resurrect-Time: 0
        Other-Leg-Channel-Bridged-Time: 0
        Other-Leg-Channel-Last-Hold: 0
        Other-Leg-Channel-Hold-Accum: 0
        Other-Leg-Screen-Bit: true
        Other-Leg-Privacy-Hide-Name: false
        Other-Leg-Privacy-Hide-Number: false
        DTMF-Digit: 5
        DTMF-Duration: 1200
        DTMF-Source: RTP

CHANNEL_CREATE
++++++++++++++

Channel create is sent when an extension is going to do something. It can either be dialing someone or it can be an incoming call to an extension.

**Example**::

        Event-Name: CHANNEL_CREATE
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:38:15
        Event-Date-GMT: Fri, 15 Jul 2016 08:38:15 GMT
        Event-Date-Timestamp: 1468571895627235
        Event-Calling-File: switch_core_state_machine.c
        Event-Calling-Function: switch_core_session_run
        Event-Calling-Line-Number: 588
        Event-Sequence: 333663
        Channel-State: CS_INIT
        Channel-Call-State: DOWN
        Channel-State-Number: 2
        Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Unique-ID: 61c4a5a3-ce44-4e65-b390-943dccdfe77f
        Call-Direction: inbound
        Presence-Call-Direction: inbound
        Channel-HIT-Dialplan: true
        Channel-Presence-ID: 9999@demo.webitel.com
        Channel-Call-UUID: 61c4a5a3-ce44-4e65-b390-943dccdfe77f
        Answer-State: ringing
        Channel-Read-Codec-Name: PCMU
        Channel-Read-Codec-Rate: 8000
        Channel-Read-Codec-Bit-Rate: 64000
        Channel-Write-Codec-Name: PCMU
        Channel-Write-Codec-Rate: 8000
        Channel-Write-Codec-Bit-Rate: 64000
        Caller-Direction: inbound
        Caller-Logical-Direction: inbound
        Caller-Username: 9999
        Caller-Dialplan: XML
        Caller-Caller-ID-Name: Igor
        Caller-Caller-ID-Number: 9999
        Caller-Orig-Caller-ID-Name: Igor
        Caller-Orig-Caller-ID-Number: 9999
        Caller-Network-Addr: 10.10.10.107
        Caller-ANI: 9999
        Caller-Destination-Number: 100
        Caller-Unique-ID: 61c4a5a3-ce44-4e65-b390-943dccdfe77f
        Caller-Source: mod_sofia
        Caller-Context: default
        Caller-Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Caller-Profile-Index: 1
        Caller-Profile-Created-Time: 1468571895627235
        Caller-Channel-Created-Time: 1468571895627235
        Caller-Channel-Answered-Time: 0
        Caller-Channel-Progress-Time: 0
        Caller-Channel-Progress-Media-Time: 0
        Caller-Channel-Hangup-Time: 0
        Caller-Channel-Transfer-Time: 0
        Caller-Channel-Resurrect-Time: 0
        Caller-Channel-Bridged-Time: 0
        Caller-Channel-Last-Hold: 0
        Caller-Channel-Hold-Accum: 0
        Caller-Screen-Bit: true
        Caller-Privacy-Hide-Name: false
        Caller-Privacy-Hide-Number: false
        variable_direction: inbound
        variable_uuid: 61c4a5a3-ce44-4e65-b390-943dccdfe77f
        variable_call_uuid: 61c4a5a3-ce44-4e65-b390-943dccdfe77f
        variable_session_id: 255
        variable_sip_from_user: 9999
        variable_sip_from_port: 5070
        variable_sip_from_uri: 9999@demo.webitel.com:5070
        variable_sip_from_host: demo.webitel.com
        variable_video_media_flow: sendrecv
        variable_channel_name: sofia/internal/9999@demo.webitel.com:5070
        variable_sip_call_id: 2526957462@10.10.10.107
        variable_ep_codec_string: CORE_PCM_MODULE.PCMU@8000h@20i@64000b,CORE_PCM_MODULE.PCMA@8000h@20i@64000b,mod_bcg729.G729@8000h@20i@8000b,mod_spandsp.G722@8000h@20i@64000b
        variable_sip_local_network_addr: 194.44.1.1
        variable_sip_network_ip: 10.10.10.107
        variable_sip_network_port: 5062
        variable_sip_received_ip: 10.10.10.107
        variable_sip_received_port: 5062
        variable_sip_via_protocol: udp
        variable_sip_authorized: true
        variable_Event-Name: REQUEST_PARAMS
        variable_Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        variable_FreeSWITCH-Hostname: pre.webitel.com
        variable_FreeSWITCH-Switchname: webitel
        variable_FreeSWITCH-IPv4: 194.44.1.1
        variable_FreeSWITCH-IPv6: 2a00:fc00::1
        variable_Event-Date-Local: 2016-07-15 08:38:15
        variable_Event-Date-GMT: Fri, 15 Jul 2016 08:38:15 GMT
        variable_Event-Date-Timestamp: 1468571895627235
        variable_Event-Calling-File: sofia.c
        variable_Event-Calling-Function: sofia_handle_sip_i_invite
        variable_Event-Calling-Line-Number: 9670
        variable_Event-Sequence: 333657
        variable_sip_number_alias: 9999
        variable_sip_auth_username: 9999
        variable_sip_auth_realm: demo.webitel.com
        variable_number_alias: 9999
        variable_requested_user_name: 9999
        variable_requested_domain_name: demo.webitel.com
        variable_customer_id: igor
        variable_default_language: en
        variable_kk: kk
        variable_dsdada: das
        variable_w_domain: demo.webitel.com
        variable_user_scheme: account
        variable_user_context: default
        variable_effective_caller_id_name: 9999
        variable_outbound_caller_id_name: 9999
        variable_account_role: user
        variable_skills: 1,2,3,4,5,6,7
        variable_account_state: onhook
        variable_account_status: none
        variable_user_name: 9999
        variable_domain_name: demo.webitel.com
        variable_sip_from_user_stripped: 9999
        variable_sip_from_tag: 1040489445
        variable_sofia_profile_name: internal
        variable_recovery_profile_name: internal
        variable_sip_full_via: SIP/2.0/UDP 10.10.10.107:5062;branch=z9hG4bK2551340570
        variable_sip_from_display: Igor
        variable_sip_full_from: "Igor" <sip:9999@demo.webitel.com:5070>;tag=1040489445
        variable_sip_full_to: <sip:100@demo.webitel.com:5070>
        variable_sip_req_user: 100
        variable_sip_req_port: 5070
        variable_sip_req_uri: 100@demo.webitel.com:5070
        variable_sip_req_host: demo.webitel.com
        variable_sip_to_user: 100
        variable_sip_to_port: 5070
        variable_sip_to_uri: 100@demo.webitel.com:5070
        variable_sip_to_host: demo.webitel.com
        variable_sip_contact_user: 9999
        variable_sip_contact_port: 5062
        variable_sip_contact_uri: 9999@10.10.10.107:5062
        variable_sip_contact_host: 10.10.10.107
        variable_sip_user_agent: Yealink SIP-T26P 6.73.0.50
        variable_sip_via_host: 10.10.10.107
        variable_sip_via_port: 5062
        variable_max_forwards: 70
        variable_presence_id: 9999@demo.webitel.com
        variable_switch_r_sdp: v=0
        o=- 20100 20100 IN IP4 10.10.10.107
        s=SDP data
        c=IN IP4 10.10.10.107
        t=0 0
        m=audio 11780 RTP/AVP 0 8 18 9 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:8 PCMA/8000
        a=rtpmap:18 G729/8000
        a=fmtp:18 annexb=no
        a=rtpmap:9 G722/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20

        variable_audio_media_flow: sendrecv
        variable_rtp_use_codec_string: OPUS,G722,PCMA,PCMU,GSM,G729,ilbc,VP8,VP9,H264,H263,H263-1998
        variable_remote_media_ip: 10.10.10.107
        variable_remote_media_port: 11780
        variable_rtp_audio_recv_pt: 0
        variable_rtp_use_codec_name: PCMU
        variable_rtp_use_codec_rate: 8000
        variable_rtp_use_codec_ptime: 20
        variable_rtp_use_codec_channels: 1
        variable_rtp_last_audio_codec_string: PCMU@8000h@20i@1c
        variable_read_codec: PCMU
        variable_original_read_codec: PCMU
        variable_read_rate: 8000
        variable_original_read_rate: 8000
        variable_write_codec: PCMU
        variable_write_rate: 8000
        variable_dtmf_type: rfc2833
        variable_endpoint_disposition: RECEIVED

CHANNEL_DESTROY
+++++++++++++++

Called when a channel should get destroyed.

**Example**::

        Event-Name: CHANNEL_DESTROY
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:47:26
        Event-Date-GMT: Fri, 15 Jul 2016 08:47:26 GMT
        Event-Date-Timestamp: 1468572446707176
        Event-Calling-File: switch_core_session.c
        Event-Calling-Function: switch_core_session_perform_destroy
        Event-Calling-Line-Number: 1497
        Event-Sequence: 334284
        Channel-State: CS_REPORTING
        Channel-Call-State: HANGUP
        Channel-State-Number: 12
        Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Unique-ID: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c
        Call-Direction: inbound
        Presence-Call-Direction: inbound
        Channel-HIT-Dialplan: true
        Channel-Presence-ID: 9999@demo.webitel.com
        Channel-Presence-Data: demo.webitel.com
        Channel-Call-UUID: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c
        Answer-State: hangup
        Hangup-Cause: NORMAL_CLEARING
        Channel-Read-Codec-Name: PCMU
        Channel-Read-Codec-Rate: 8000
        Channel-Read-Codec-Bit-Rate: 64000
        Channel-Write-Codec-Name: PCMU
        Channel-Write-Codec-Rate: 8000
        Channel-Write-Codec-Bit-Rate: 64000
        Caller-Direction: inbound
        Caller-Logical-Direction: inbound
        Caller-Username: 9999
        Caller-Dialplan: XML
        Caller-Caller-ID-Name: Igor
        Caller-Caller-ID-Number: 9999
        Caller-Orig-Caller-ID-Name: Igor
        Caller-Orig-Caller-ID-Number: 9999
        Caller-Callee-ID-Name: Outbound Call
        Caller-Callee-ID-Number: 100
        Caller-Network-Addr: 10.10.10.107
        Caller-ANI: 9999
        Caller-Destination-Number: 100
        Caller-Unique-ID: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c
        Caller-Source: mod_sofia
        Caller-Context: default
        Caller-Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Caller-Profile-Index: 1
        Caller-Profile-Created-Time: 1468572421547178
        Caller-Channel-Created-Time: 1468572421547178
        Caller-Channel-Answered-Time: 1468572430647185
        Caller-Channel-Progress-Time: 1468572421827233
        Caller-Channel-Progress-Media-Time: 1468572421587234
        Caller-Channel-Hangup-Time: 1468572446687211
        Caller-Channel-Transfer-Time: 0
        Caller-Channel-Resurrect-Time: 0
        Caller-Channel-Bridged-Time: 1468572430667190
        Caller-Channel-Last-Hold: 0
        Caller-Channel-Hold-Accum: 0
        Caller-Screen-Bit: true
        Caller-Privacy-Hide-Name: false
        Caller-Privacy-Hide-Number: false
        Other-Type: originatee
        Other-Leg-Direction: outbound
        Other-Leg-Logical-Direction: inbound
        Other-Leg-Username: 9999
        Other-Leg-Dialplan: XML
        Other-Leg-Caller-ID-Name: 9999
        Other-Leg-Caller-ID-Number: 9999
        Other-Leg-Orig-Caller-ID-Name: Igor
        Other-Leg-Orig-Caller-ID-Number: 9999
        Other-Leg-Callee-ID-Name: Outbound Call
        Other-Leg-Callee-ID-Number: 100
        Other-Leg-Network-Addr: 10.10.10.101
        Other-Leg-ANI: 9999
        Other-Leg-Destination-Number: 100
        Other-Leg-Unique-ID: 2af264d8-f7c0-48aa-ab32-e8d042463db0
        Other-Leg-Source: mod_sofia
        Other-Leg-Context: default
        Other-Leg-Channel-Name: sofia/internal/100@10.10.10.101:5064
        Other-Leg-Profile-Created-Time: 1468572421607175
        Other-Leg-Channel-Created-Time: 1468572421607175
        Other-Leg-Channel-Answered-Time: 1468572430647185
        Other-Leg-Channel-Progress-Time: 1468572421827233
        Other-Leg-Channel-Progress-Media-Time: 0
        Other-Leg-Channel-Hangup-Time: 0
        Other-Leg-Channel-Transfer-Time: 0
        Other-Leg-Channel-Resurrect-Time: 0
        Other-Leg-Channel-Bridged-Time: 0
        Other-Leg-Channel-Last-Hold: 0
        Other-Leg-Channel-Hold-Accum: 0
        Other-Leg-Screen-Bit: true
        Other-Leg-Privacy-Hide-Name: false
        Other-Leg-Privacy-Hide-Number: false
        variable_direction: inbound
        variable_uuid: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c
        variable_session_id: 259
        variable_sip_from_user: 9999
        variable_sip_from_port: 5070
        variable_sip_from_uri: 9999@demo.webitel.com:5070
        variable_sip_from_host: demo.webitel.com
        variable_video_media_flow: sendrecv
        variable_channel_name: sofia/internal/9999@demo.webitel.com:5070
        variable_ep_codec_string: CORE_PCM_MODULE.PCMU@8000h@20i@64000b,CORE_PCM_MODULE.PCMA@8000h@20i@64000b,mod_bcg729.G729@8000h@20i@8000b,mod_spandsp.G722@8000h@20i@64000b
        variable_sip_local_network_addr: 194.44.1.1
        variable_sip_network_ip: 10.10.10.107
        variable_sip_network_port: 5062
        variable_sip_received_ip: 10.10.10.107
        variable_sip_received_port: 5062
        variable_sip_via_protocol: udp
        variable_sip_authorized: true
        variable_Event-Name: REQUEST_PARAMS
        variable_Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        variable_FreeSWITCH-Hostname: pre.webitel.com
        variable_FreeSWITCH-Switchname: webitel
        variable_FreeSWITCH-IPv4: 194.44.1.1
        variable_FreeSWITCH-IPv6: 2a00:fc00::1
        variable_Event-Date-Local: 2016-07-15 08:47:01
        variable_Event-Date-GMT: Fri, 15 Jul 2016 08:47:01 GMT
        variable_Event-Date-Timestamp: 1468572421527202
        variable_Event-Calling-File: sofia.c
        variable_Event-Calling-Function: sofia_handle_sip_i_invite
        variable_Event-Calling-Line-Number: 9670
        variable_Event-Sequence: 334145
        variable_sip_number_alias: 9999
        variable_sip_auth_username: 9999
        variable_sip_auth_realm: demo.webitel.com
        variable_number_alias: 9999
        variable_requested_user_name: 9999
        variable_requested_domain_name: demo.webitel.com
        variable_customer_id: igor
        variable_default_language: en
        variable_kk: kk
        variable_dsdada: das
        variable_w_domain: demo.webitel.com
        variable_user_scheme: account
        variable_user_context: default
        variable_effective_caller_id_name: 9999
        variable_outbound_caller_id_name: 9999
        variable_account_role: user
        variable_skills: 1,2,3,4,5,6,7
        variable_account_state: onhook
        variable_account_status: none
        variable_user_name: 9999
        variable_sip_from_user_stripped: 9999
        variable_sofia_profile_name: internal
        variable_recovery_profile_name: internal
        variable_sip_req_user: 100
        variable_sip_req_port: 5070
        variable_sip_req_uri: 100@demo.webitel.com:5070
        variable_sip_req_host: demo.webitel.com
        variable_sip_to_user: 100
        variable_sip_to_port: 5070
        variable_sip_to_uri: 100@demo.webitel.com:5070
        variable_sip_to_host: demo.webitel.com
        variable_sip_contact_user: 9999
        variable_sip_contact_port: 5062
        variable_sip_contact_uri: 9999@10.10.10.107:5062
        variable_sip_contact_host: 10.10.10.107
        variable_sip_user_agent: Yealink SIP-T26P 6.73.0.50
        variable_sip_via_host: 10.10.10.107
        variable_sip_via_port: 5062
        variable_max_forwards: 70
        variable_presence_id: 9999@demo.webitel.com
        variable_audio_media_flow: sendrecv
        variable_rtp_use_codec_string: OPUS,G722,PCMA,PCMU,GSM,G729,ilbc,VP8,VP9,H264,H263,H263-1998
        variable_rtp_use_codec_name: PCMU
        variable_rtp_use_codec_rate: 8000
        variable_rtp_use_codec_ptime: 20
        variable_rtp_use_codec_channels: 1
        variable_rtp_last_audio_codec_string: PCMU@8000h@20i@1c
        variable_original_read_codec: PCMU
        variable_original_read_rate: 8000
        variable_write_codec: PCMU
        variable_write_rate: 8000
        variable_domain_name: demo.webitel.com
        variable_call_uuid: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c
        variable_socket_host: 10.10.10.25
        variable_sound_prefix: //sounds/en/us/callie
        variable_webitel_direction: internal
        variable_dialed_extension: 100
        variable_export_vars: dialed_extension
        variable_eavesdrop_group: demo.webitel.com
        variable_presence_data: demo.webitel.com
        variable_ringback: %(2000,4000,440,480)
        variable_transfer_ringback: %(400,200,400,450);%(400,2000,400,450)
        variable_hangup_after_bridge: true
        variable_continue_on_fail: true
        variable_webitel_record_file_name: 45d52500-06bd-4cd1-b0d0-ddcf18c7105c_recordSession.mp3
        variable_RECORD_MIN_SEC: 2
        variable_RECORD_STEREO: true
        variable_RECORD_BRIDGE_REQ: true
        variable_recording_follow_transfer: true
        variable_record_post_process_exec_api: luarun:RecordUpload.lua 45d52500-06bd-4cd1-b0d0-ddcf18c7105c demo.webitel.com mp3 none recordSession
        variable_local_media_ip: 194.44.1.1
        variable_local_media_port: 19312
        variable_advertised_media_ip: 194.44.1.1
        variable_rtp_use_timer_name: soft
        variable_rtp_use_pt: 0
        variable_rtp_use_ssrc: 730645669
        variable_current_application_data: {domain_name=demo.webitel.com}user/100@demo.webitel.com
        variable_current_application: bridge
        variable_dialed_user: 100
        variable_dialed_domain: demo.webitel.com
        variable_originated_legs: ARRAY::2af264d8-f7c0-48aa-ab32-e8d042463db0;Outbound Call;100|:2af264d8-f7c0-48aa-ab32-e8d042463db0;Outbound Call;100
        variable_zrtp_secure_media_confirmed_audio: false
        variable_read_codec: PCMU
        variable_read_rate: 8000
        variable_endpoint_disposition: ANSWER
        variable_originate_causes: ARRAY::2af264d8-f7c0-48aa-ab32-e8d042463db0;NONE|:2af264d8-f7c0-48aa-ab32-e8d042463db0;NONE
        variable_originate_disposition: SUCCESS
        variable_DIALSTATUS: SUCCESS
        variable_last_bridge_to: 2af264d8-f7c0-48aa-ab32-e8d042463db0
        variable_bridge_channel: sofia/internal/100@10.10.10.101:5064
        variable_bridge_uuid: 2af264d8-f7c0-48aa-ab32-e8d042463db0
        variable_signal_bond: 2af264d8-f7c0-48aa-ab32-e8d042463db0
        variable_sip_to_tag: a1Sy27DgyvFBQ
        variable_sip_from_tag: 3861088024
        variable_sip_cseq: 2
        variable_sip_call_id: 1479889331@10.10.10.107
        variable_sip_full_via: SIP/2.0/UDP 10.10.10.107:5062;branch=z9hG4bK339930588
        variable_sip_from_display: Igor
        variable_sip_full_from: "Igor" <sip:9999@demo.webitel.com:5070>;tag=3861088024
        variable_sip_full_to: <sip:100@demo.webitel.com:5070>;tag=a1Sy27DgyvFBQ
        variable_last_sent_callee_id_name: Outbound Call
        variable_last_sent_callee_id_number: 100
        variable_switch_r_sdp: v=0
        o=- 20104 20105 IN IP4 10.10.10.107
        s=SDP data
        c=IN IP4 10.10.10.107
        t=0 0
        a=sendrecv
        m=audio 11788 RTP/AVP 0 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20

        variable_remote_media_ip: 10.10.10.107
        variable_remote_media_port: 11788
        variable_rtp_audio_recv_pt: 0
        variable_dtmf_type: rfc2833
        variable_rtp_2833_send_payload: 101
        variable_rtp_2833_recv_payload: 101
        variable_rtp_local_sdp_str: v=0
        o=webitel 1468553109 1468553112 IN IP4 194.44.1.1
        s=webitel
        c=IN IP4 194.44.1.1
        t=0 0
        m=audio 19312 RTP/AVP 0 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-16
        a=ptime:20
        a=sendrecv

        variable_switch_m_sdp: v=0
        o=- 20131 20132 IN IP4 10.10.10.101
        s=SDP data
        c=IN IP4 10.10.10.101
        t=0 0
        m=audio 11782 RTP/AVP 9 101
        a=rtpmap:9 G722/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20
        m=video 0 RTP/AVP 104

        variable_sip_hangup_phrase: OK
        variable_last_bridge_hangup_cause: NORMAL_CLEARING
        variable_last_bridge_proto_specific_hangup_cause: sip:200
        variable_bridge_hangup_cause: NORMAL_CLEARING
        variable_record_samples: 128320
        variable_record_seconds: 16
        variable_record_ms: 16040
        variable_record_completion_cause: success-silence
        variable_hangup_cause: NORMAL_CLEARING
        variable_hangup_cause_q850: 16
        variable_digits_dialed: none
        variable_start_stamp: 2016-07-15 08:47:01
        variable_profile_start_stamp: 2016-07-15 08:47:01
        variable_answer_stamp: 2016-07-15 08:47:10
        variable_bridge_stamp: 2016-07-15 08:47:10
        variable_progress_stamp: 2016-07-15 08:47:01
        variable_progress_media_stamp: 2016-07-15 08:47:01
        variable_end_stamp: 2016-07-15 08:47:26
        variable_start_epoch: 1468572421
        variable_start_uepoch: 1468572421547178
        variable_profile_start_epoch: 1468572421
        variable_profile_start_uepoch: 1468572421547178
        variable_answer_epoch: 1468572430
        variable_answer_uepoch: 1468572430647185
        variable_bridge_epoch: 1468572430
        variable_bridge_uepoch: 1468572430667190
        variable_last_hold_epoch: 0
        variable_last_hold_uepoch: 0
        variable_hold_accum_seconds: 0
        variable_hold_accum_usec: 0
        variable_hold_accum_ms: 0
        variable_resurrect_epoch: 0
        variable_resurrect_uepoch: 0
        variable_progress_epoch: 1468572421
        variable_progress_uepoch: 1468572421827233
        variable_progress_media_epoch: 1468572421
        variable_progress_media_uepoch: 1468572421587234
        variable_end_epoch: 1468572446
        variable_end_uepoch: 1468572446687211
        variable_last_app: bridge
        variable_last_arg: {domain_name=demo.webitel.com}user/100@demo.webitel.com
        variable_caller_id: "Igor" <9999>
        variable_duration: 25
        variable_billsec: 16
        variable_progresssec: 0
        variable_answersec: 9
        variable_waitsec: 9
        variable_progress_mediasec: 0
        variable_flow_billsec: 25
        variable_mduration: 25140
        variable_billmsec: 16040
        variable_progressmsec: 280
        variable_answermsec: 9100
        variable_waitmsec: 9120
        variable_progress_mediamsec: 40
        variable_flow_billmsec: 25140
        variable_uduration: 25140033
        variable_billusec: 16040026
        variable_progressusec: 280055
        variable_answerusec: 9100007
        variable_waitusec: 9120012
        variable_progress_mediausec: 40056
        variable_flow_billusec: 25140033
        variable_sip_hangup_disposition: send_bye
        variable_rtp_audio_in_raw_bytes: 214656
        variable_rtp_audio_in_media_bytes: 214656
        variable_rtp_audio_in_packet_count: 1248
        variable_rtp_audio_in_media_packet_count: 1248
        variable_rtp_audio_in_skip_packet_count: 9
        variable_rtp_audio_in_jitter_packet_count: 0
        variable_rtp_audio_in_dtmf_packet_count: 0
        variable_rtp_audio_in_cng_packet_count: 0
        variable_rtp_audio_in_flush_packet_count: 0
        variable_rtp_audio_in_largest_jb_size: 0
        variable_rtp_audio_in_jitter_min_variance: 12.12
        variable_rtp_audio_in_jitter_max_variance: 400.00
        variable_rtp_audio_in_jitter_loss_rate: 0.00
        variable_rtp_audio_in_jitter_burst_rate: 0.00
        variable_rtp_audio_in_mean_interval: 20.00
        variable_rtp_audio_in_flaw_total: 0
        variable_rtp_audio_in_quality_percentage: 100.00
        variable_rtp_audio_in_mos: 4.50
        variable_rtp_audio_out_raw_bytes: 213624
        variable_rtp_audio_out_media_bytes: 213624
        variable_rtp_audio_out_packet_count: 1242
        variable_rtp_audio_out_media_packet_count: 1242
        variable_rtp_audio_out_skip_packet_count: 0
        variable_rtp_audio_out_dtmf_packet_count: 0
        variable_rtp_audio_out_cng_packet_count: 0
        variable_rtp_audio_rtcp_packet_count: 0
        variable_rtp_audio_rtcp_octet_count: 0

CHANNEL_BRIDGE
++++++++++++++

A call is being bridged between two endpoints.

**Example**::

        Event-Name: CHANNEL_BRIDGE
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:56:06
        Event-Date-GMT: Fri, 15 Jul 2016 08:56:06 GMT
        Event-Date-Timestamp: 1468572966127390
        Event-Calling-File: switch_ivr_bridge.c
        Event-Calling-Function: switch_ivr_multi_threaded_bridge
        Event-Calling-Line-Number: 1501
        Event-Sequence: 334590
        Bridge-A-Unique-ID: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        Bridge-B-Unique-ID: 88e739f2-0984-4c2c-af9d-7e8fe9a8398f
        Channel-State: CS_EXECUTE
        Channel-Call-State: ACTIVE
        Channel-State-Number: 4
        Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Unique-ID: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        Call-Direction: inbound
        Presence-Call-Direction: inbound
        Channel-HIT-Dialplan: true
        Channel-Presence-ID: 9999@demo.webitel.com
        Channel-Presence-Data: demo.webitel.com
        Channel-Call-UUID: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        Answer-State: answered
        Channel-Read-Codec-Name: PCMU
        Channel-Read-Codec-Rate: 8000
        Channel-Read-Codec-Bit-Rate: 64000
        Channel-Write-Codec-Name: PCMU
        Channel-Write-Codec-Rate: 8000
        Channel-Write-Codec-Bit-Rate: 64000
        Caller-Direction: inbound
        Caller-Logical-Direction: inbound
        Caller-Username: 9999
        Caller-Dialplan: XML
        Caller-Caller-ID-Name: Igor
        Caller-Caller-ID-Number: 9999
        Caller-Orig-Caller-ID-Name: Igor
        Caller-Orig-Caller-ID-Number: 9999
        Caller-Callee-ID-Name: Outbound Call
        Caller-Callee-ID-Number: 100
        Caller-Network-Addr: 10.10.10.107
        Caller-ANI: 9999
        Caller-Destination-Number: 100
        Caller-Unique-ID: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        Caller-Source: mod_sofia
        Caller-Context: default
        Caller-Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Caller-Profile-Index: 1
        Caller-Profile-Created-Time: 1468572961407256
        Caller-Channel-Created-Time: 1468572961407256
        Caller-Channel-Answered-Time: 1468572966127390
        Caller-Channel-Progress-Time: 1468572961627239
        Caller-Channel-Progress-Media-Time: 1468572961487204
        Caller-Channel-Hangup-Time: 0
        Caller-Channel-Transfer-Time: 0
        Caller-Channel-Resurrect-Time: 0
        Caller-Channel-Bridged-Time: 1468572966127390
        Caller-Channel-Last-Hold: 0
        Caller-Channel-Hold-Accum: 0
        Caller-Screen-Bit: true
        Caller-Privacy-Hide-Name: false
        Caller-Privacy-Hide-Number: false
        Other-Type: originatee
        Other-Leg-Direction: outbound
        Other-Leg-Logical-Direction: inbound
        Other-Leg-Username: 9999
        Other-Leg-Dialplan: XML
        Other-Leg-Caller-ID-Name: 9999
        Other-Leg-Caller-ID-Number: 9999
        Other-Leg-Orig-Caller-ID-Name: Igor
        Other-Leg-Orig-Caller-ID-Number: 9999
        Other-Leg-Callee-ID-Name: Outbound Call
        Other-Leg-Callee-ID-Number: 100
        Other-Leg-Network-Addr: 10.10.10.101
        Other-Leg-ANI: 9999
        Other-Leg-Destination-Number: 100
        Other-Leg-Unique-ID: 88e739f2-0984-4c2c-af9d-7e8fe9a8398f
        Other-Leg-Source: mod_sofia
        Other-Leg-Context: default
        Other-Leg-Channel-Name: sofia/internal/100@10.10.10.101:5064
        Other-Leg-Profile-Created-Time: 1468572961507188
        Other-Leg-Channel-Created-Time: 1468572961507188
        Other-Leg-Channel-Answered-Time: 1468572966107185
        Other-Leg-Channel-Progress-Time: 1468572961627239
        Other-Leg-Channel-Progress-Media-Time: 0
        Other-Leg-Channel-Hangup-Time: 0
        Other-Leg-Channel-Transfer-Time: 0
        Other-Leg-Channel-Resurrect-Time: 0
        Other-Leg-Channel-Bridged-Time: 0
        Other-Leg-Channel-Last-Hold: 0
        Other-Leg-Channel-Hold-Accum: 0
        Other-Leg-Screen-Bit: true
        Other-Leg-Privacy-Hide-Name: false
        Other-Leg-Privacy-Hide-Number: false
        variable_direction: inbound
        variable_uuid: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        variable_session_id: 261
        variable_sip_from_user: 9999
        variable_sip_from_port: 5070
        variable_sip_from_uri: 9999@demo.webitel.com:5070
        variable_sip_from_host: demo.webitel.com
        variable_video_media_flow: sendrecv
        variable_channel_name: sofia/internal/9999@demo.webitel.com:5070
        variable_sip_call_id: 1142818458@10.10.10.107
        variable_ep_codec_string: CORE_PCM_MODULE.PCMU@8000h@20i@64000b,CORE_PCM_MODULE.PCMA@8000h@20i@64000b,mod_bcg729.G729@8000h@20i@8000b,mod_spandsp.G722@8000h@20i@64000b
        variable_sip_local_network_addr: 194.44.1.1
        variable_sip_network_ip: 10.10.10.107
        variable_sip_network_port: 5062
        variable_sip_received_ip: 10.10.10.107
        variable_sip_received_port: 5062
        variable_sip_via_protocol: udp
        variable_sip_authorized: true
        variable_Event-Name: REQUEST_PARAMS
        variable_Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        variable_FreeSWITCH-Hostname: pre.webitel.com
        variable_FreeSWITCH-Switchname: webitel
        variable_FreeSWITCH-IPv4: 194.44.1.1
        variable_FreeSWITCH-IPv6: 2a00:fc00::1
        variable_Event-Date-Local: 2016-07-15 08:56:01
        variable_Event-Date-GMT: Fri, 15 Jul 2016 08:56:01 GMT
        variable_Event-Date-Timestamp: 1468572961407256
        variable_Event-Calling-File: sofia.c
        variable_Event-Calling-Function: sofia_handle_sip_i_invite
        variable_Event-Calling-Line-Number: 9670
        variable_Event-Sequence: 334498
        variable_sip_number_alias: 9999
        variable_sip_auth_username: 9999
        variable_sip_auth_realm: demo.webitel.com
        variable_number_alias: 9999
        variable_requested_user_name: 9999
        variable_requested_domain_name: demo.webitel.com
        variable_customer_id: igor
        variable_default_language: en
        variable_kk: kk
        variable_dsdada: das
        variable_w_domain: demo.webitel.com
        variable_user_scheme: account
        variable_user_context: default
        variable_effective_caller_id_name: 9999
        variable_outbound_caller_id_name: 9999
        variable_account_role: user
        variable_skills: 1,2,3,4,5,6,7
        variable_account_state: onhook
        variable_account_status: none
        variable_user_name: 9999
        variable_sip_from_user_stripped: 9999
        variable_sip_from_tag: 3102318183
        variable_sofia_profile_name: internal
        variable_recovery_profile_name: internal
        variable_sip_full_via: SIP/2.0/UDP 10.10.10.107:5062;branch=z9hG4bK1537080004
        variable_sip_from_display: Igor
        variable_sip_full_from: "Igor" <sip:9999@demo.webitel.com:5070>;tag=3102318183
        variable_sip_full_to: <sip:100@demo.webitel.com:5070>
        variable_sip_req_user: 100
        variable_sip_req_port: 5070
        variable_sip_req_uri: 100@demo.webitel.com:5070
        variable_sip_req_host: demo.webitel.com
        variable_sip_to_user: 100
        variable_sip_to_port: 5070
        variable_sip_to_uri: 100@demo.webitel.com:5070
        variable_sip_to_host: demo.webitel.com
        variable_sip_contact_user: 9999
        variable_sip_contact_port: 5062
        variable_sip_contact_uri: 9999@10.10.10.107:5062
        variable_sip_contact_host: 10.10.10.107
        variable_sip_user_agent: Yealink SIP-T26P 6.73.0.50
        variable_sip_via_host: 10.10.10.107
        variable_sip_via_port: 5062
        variable_max_forwards: 70
        variable_presence_id: 9999@demo.webitel.com
        variable_switch_r_sdp: v=0
        o=- 20105 20105 IN IP4 10.10.10.107
        s=SDP data
        c=IN IP4 10.10.10.107
        t=0 0
        m=audio 11790 RTP/AVP 0 8 18 9 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:8 PCMA/8000
        a=rtpmap:18 G729/8000
        a=fmtp:18 annexb=no
        a=rtpmap:9 G722/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20

        variable_audio_media_flow: sendrecv
        variable_rtp_use_codec_string: OPUS,G722,PCMA,PCMU,GSM,G729,ilbc,VP8,VP9,H264,H263,H263-1998
        variable_rtp_audio_recv_pt: 0
        variable_rtp_use_codec_name: PCMU
        variable_rtp_use_codec_rate: 8000
        variable_rtp_use_codec_ptime: 20
        variable_rtp_use_codec_channels: 1
        variable_rtp_last_audio_codec_string: PCMU@8000h@20i@1c
        variable_original_read_codec: PCMU
        variable_original_read_rate: 8000
        variable_write_codec: PCMU
        variable_write_rate: 8000
        variable_dtmf_type: rfc2833
        variable_domain_name: demo.webitel.com
        variable_call_uuid: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9
        variable_socket_host: 10.10.10.25
        variable_sound_prefix: //sounds/en/us/callie
        variable_webitel_direction: internal
        variable_dialed_extension: 100
        variable_export_vars: dialed_extension
        variable_eavesdrop_group: demo.webitel.com
        variable_presence_data: demo.webitel.com
        variable_ringback: %(2000,4000,440,480)
        variable_transfer_ringback: %(400,200,400,450);%(400,2000,400,450)
        variable_hangup_after_bridge: true
        variable_continue_on_fail: true
        variable_webitel_record_file_name: 9c7e3d82-3c0d-4259-ad37-e534003f9ad9_recordSession.mp3
        variable_RECORD_MIN_SEC: 2
        variable_RECORD_STEREO: true
        variable_RECORD_BRIDGE_REQ: true
        variable_recording_follow_transfer: true
        variable_record_post_process_exec_api: luarun:RecordUpload.lua 9c7e3d82-3c0d-4259-ad37-e534003f9ad9 demo.webitel.com mp3 none recordSession
        variable_local_media_ip: 194.44.1.1
        variable_local_media_port: 19340
        variable_advertised_media_ip: 194.44.1.1
        variable_rtp_use_timer_name: soft
        variable_rtp_use_pt: 0
        variable_rtp_use_ssrc: 730683089
        variable_rtp_2833_send_payload: 101
        variable_rtp_2833_recv_payload: 101
        variable_remote_media_ip: 10.10.10.107
        variable_remote_media_port: 11790
        variable_current_loop: 1
        variable_total_loops: 1
        variable_current_application_data: {domain_name=demo.webitel.com}user/100@demo.webitel.com
        variable_current_application: bridge
        variable_dialed_user: 100
        variable_dialed_domain: demo.webitel.com
        variable_originated_legs: ARRAY::88e739f2-0984-4c2c-af9d-7e8fe9a8398f;Outbound Call;100|:88e739f2-0984-4c2c-af9d-7e8fe9a8398f;Outbound Call;100
        variable_zrtp_secure_media_confirmed_audio: false
        variable_switch_m_sdp: v=0
        o=- 20132 20132 IN IP4 10.10.10.101
        s=SDP data
        c=IN IP4 10.10.10.101
        t=0 0
        m=audio 11786 RTP/AVP 9 108
        a=rtpmap:9 G722/8000
        a=rtpmap:108 telephone-event/8000
        a=fmtp:108 0-15
        a=ptime:20
        m=video 0 RTP/AVP 104 105 106 34 107
        b=AS:1024

        variable_read_codec: PCMU
        variable_read_rate: 8000
        variable_rtp_local_sdp_str: v=0
        o=webitel 1468553621 1468553623 IN IP4 194.44.1.1
        s=webitel
        c=IN IP4 194.44.1.1
        t=0 0
        m=audio 19340 RTP/AVP 0 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-16
        a=ptime:20
        a=sendrecv

        variable_endpoint_disposition: ANSWER
        variable_originate_causes: ARRAY::88e739f2-0984-4c2c-af9d-7e8fe9a8398f;NONE|:88e739f2-0984-4c2c-af9d-7e8fe9a8398f;NONE
        variable_originate_disposition: SUCCESS
        variable_DIALSTATUS: SUCCESS
        variable_signal_bond: 88e739f2-0984-4c2c-af9d-7e8fe9a8398f

CHANNEL_UNBRIDGE
++++++++++++++++

A bridge has been terminated. The call itself will most probably be terminated since bridges exist during a call's lifespan.

**Example**::

        Event-Name: CHANNEL_UNBRIDGE
        Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        FreeSWITCH-Hostname: pre.webitel.com
        FreeSWITCH-Switchname: webitel
        FreeSWITCH-IPv4: 194.44.1.1
        FreeSWITCH-IPv6: 2a00:fc00::1
        Event-Date-Local: 2016-07-15 08:58:10
        Event-Date-GMT: Fri, 15 Jul 2016 08:58:10 GMT
        Event-Date-Timestamp: 1468573090467299
        Event-Calling-File: switch_ivr_bridge.c
        Event-Calling-Function: switch_ivr_multi_threaded_bridge
        Event-Calling-Line-Number: 1686
        Event-Sequence: 334787
        Bridge-A-Unique-ID: d3463081-212b-4d54-b93d-63720cc9d665
        Bridge-B-Unique-ID: 1f4a8f90-d9b9-4699-a645-eb562d98b627
        Channel-State: CS_EXECUTE
        Channel-Call-State: ACTIVE
        Channel-State-Number: 4
        Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Unique-ID: d3463081-212b-4d54-b93d-63720cc9d665
        Call-Direction: inbound
        Presence-Call-Direction: inbound
        Channel-HIT-Dialplan: true
        Channel-Presence-ID: 9999@demo.webitel.com
        Channel-Presence-Data: demo.webitel.com
        Channel-Call-UUID: d3463081-212b-4d54-b93d-63720cc9d665
        Answer-State: answered
        Channel-Read-Codec-Name: PCMU
        Channel-Read-Codec-Rate: 8000
        Channel-Read-Codec-Bit-Rate: 64000
        Channel-Write-Codec-Name: PCMU
        Channel-Write-Codec-Rate: 8000
        Channel-Write-Codec-Bit-Rate: 64000
        Caller-Direction: inbound
        Caller-Logical-Direction: inbound
        Caller-Username: 9999
        Caller-Dialplan: XML
        Caller-Caller-ID-Name: Igor
        Caller-Caller-ID-Number: 9999
        Caller-Orig-Caller-ID-Name: Igor
        Caller-Orig-Caller-ID-Number: 9999
        Caller-Callee-ID-Name: Outbound Call
        Caller-Callee-ID-Number: 100
        Caller-Network-Addr: 10.10.10.107
        Caller-ANI: 9999
        Caller-Destination-Number: 100
        Caller-Unique-ID: d3463081-212b-4d54-b93d-63720cc9d665
        Caller-Source: mod_sofia
        Caller-Context: default
        Caller-Channel-Name: sofia/internal/9999@demo.webitel.com:5070
        Caller-Profile-Index: 1
        Caller-Profile-Created-Time: 1468573055707186
        Caller-Channel-Created-Time: 1468573055707186
        Caller-Channel-Answered-Time: 1468573057947208
        Caller-Channel-Progress-Time: 1468573055947205
        Caller-Channel-Progress-Media-Time: 1468573055767208
        Caller-Channel-Hangup-Time: 0
        Caller-Channel-Transfer-Time: 0
        Caller-Channel-Resurrect-Time: 0
        Caller-Channel-Bridged-Time: 1468573057947208
        Caller-Channel-Last-Hold: 0
        Caller-Channel-Hold-Accum: 0
        Caller-Screen-Bit: true
        Caller-Privacy-Hide-Name: false
        Caller-Privacy-Hide-Number: false
        Other-Type: originatee
        Other-Leg-Direction: outbound
        Other-Leg-Logical-Direction: inbound
        Other-Leg-Username: 9999
        Other-Leg-Dialplan: XML
        Other-Leg-Caller-ID-Name: 9999
        Other-Leg-Caller-ID-Number: 9999
        Other-Leg-Orig-Caller-ID-Name: Igor
        Other-Leg-Orig-Caller-ID-Number: 9999
        Other-Leg-Callee-ID-Name: Outbound Call
        Other-Leg-Callee-ID-Number: 100
        Other-Leg-Network-Addr: 10.10.10.101
        Other-Leg-ANI: 9999
        Other-Leg-Destination-Number: 100
        Other-Leg-Unique-ID: 1f4a8f90-d9b9-4699-a645-eb562d98b627
        Other-Leg-Source: mod_sofia
        Other-Leg-Context: default
        Other-Leg-Channel-Name: sofia/internal/100@10.10.10.101:5064
        Other-Leg-Profile-Created-Time: 1468573055787199
        Other-Leg-Channel-Created-Time: 1468573055787199
        Other-Leg-Channel-Answered-Time: 1468573057907238
        Other-Leg-Channel-Progress-Time: 1468573055947205
        Other-Leg-Channel-Progress-Media-Time: 0
        Other-Leg-Channel-Hangup-Time: 0
        Other-Leg-Channel-Transfer-Time: 0
        Other-Leg-Channel-Resurrect-Time: 0
        Other-Leg-Channel-Bridged-Time: 0
        Other-Leg-Channel-Last-Hold: 0
        Other-Leg-Channel-Hold-Accum: 0
        Other-Leg-Screen-Bit: true
        Other-Leg-Privacy-Hide-Name: false
        Other-Leg-Privacy-Hide-Number: false
        variable_direction: inbound
        variable_uuid: d3463081-212b-4d54-b93d-63720cc9d665
        variable_session_id: 263
        variable_sip_from_user: 9999
        variable_sip_from_port: 5070
        variable_sip_from_uri: 9999@demo.webitel.com:5070
        variable_sip_from_host: demo.webitel.com
        variable_video_media_flow: sendrecv
        variable_channel_name: sofia/internal/9999@demo.webitel.com:5070
        variable_ep_codec_string: CORE_PCM_MODULE.PCMU@8000h@20i@64000b,CORE_PCM_MODULE.PCMA@8000h@20i@64000b,mod_bcg729.G729@8000h@20i@8000b,mod_spandsp.G722@8000h@20i@64000b
        variable_sip_local_network_addr: 194.44.1.1
        variable_sip_network_ip: 10.10.10.107
        variable_sip_network_port: 5062
        variable_sip_received_ip: 10.10.10.107
        variable_sip_received_port: 5062
        variable_sip_via_protocol: udp
        variable_sip_authorized: true
        variable_Event-Name: REQUEST_PARAMS
        variable_Core-UUID: 78e8c87b-5648-47af-b339-3a3e9a31d55f
        variable_FreeSWITCH-Hostname: pre.webitel.com
        variable_FreeSWITCH-Switchname: webitel
        variable_FreeSWITCH-IPv4: 194.44.1.1
        variable_FreeSWITCH-IPv6: 2a00:fc00::1
        variable_Event-Date-Local: 2016-07-15 08:57:35
        variable_Event-Date-GMT: Fri, 15 Jul 2016 08:57:35 GMT
        variable_Event-Date-Timestamp: 1468573055707186
        variable_Event-Calling-File: sofia.c
        variable_Event-Calling-Function: sofia_handle_sip_i_invite
        variable_Event-Calling-Line-Number: 9670
        variable_Event-Sequence: 334672
        variable_sip_number_alias: 9999
        variable_sip_auth_username: 9999
        variable_sip_auth_realm: demo.webitel.com
        variable_number_alias: 9999
        variable_requested_user_name: 9999
        variable_requested_domain_name: demo.webitel.com
        variable_customer_id: igor
        variable_default_language: en
        variable_kk: kk
        variable_dsdada: das
        variable_w_domain: demo.webitel.com
        variable_user_scheme: account
        variable_user_context: default
        variable_effective_caller_id_name: 9999
        variable_outbound_caller_id_name: 9999
        variable_account_role: user
        variable_skills: 1,2,3,4,5,6,7
        variable_account_state: onhook
        variable_account_status: none
        variable_user_name: 9999
        variable_sip_from_user_stripped: 9999
        variable_sofia_profile_name: internal
        variable_recovery_profile_name: internal
        variable_sip_req_user: 100
        variable_sip_req_port: 5070
        variable_sip_req_uri: 100@demo.webitel.com:5070
        variable_sip_req_host: demo.webitel.com
        variable_sip_to_user: 100
        variable_sip_to_port: 5070
        variable_sip_to_uri: 100@demo.webitel.com:5070
        variable_sip_to_host: demo.webitel.com
        variable_sip_contact_user: 9999
        variable_sip_contact_port: 5062
        variable_sip_contact_uri: 9999@10.10.10.107:5062
        variable_sip_contact_host: 10.10.10.107
        variable_sip_user_agent: Yealink SIP-T26P 6.73.0.50
        variable_sip_via_host: 10.10.10.107
        variable_sip_via_port: 5062
        variable_max_forwards: 70
        variable_presence_id: 9999@demo.webitel.com
        variable_audio_media_flow: sendrecv
        variable_rtp_use_codec_string: OPUS,G722,PCMA,PCMU,GSM,G729,ilbc,VP8,VP9,H264,H263,H263-1998
        variable_rtp_use_codec_name: PCMU
        variable_rtp_use_codec_rate: 8000
        variable_rtp_use_codec_ptime: 20
        variable_rtp_use_codec_channels: 1
        variable_rtp_last_audio_codec_string: PCMU@8000h@20i@1c
        variable_original_read_codec: PCMU
        variable_original_read_rate: 8000
        variable_write_codec: PCMU
        variable_write_rate: 8000
        variable_domain_name: demo.webitel.com
        variable_call_uuid: d3463081-212b-4d54-b93d-63720cc9d665
        variable_socket_host: 10.10.10.25
        variable_sound_prefix: //sounds/en/us/callie
        variable_webitel_direction: internal
        variable_dialed_extension: 100
        variable_export_vars: dialed_extension
        variable_eavesdrop_group: demo.webitel.com
        variable_presence_data: demo.webitel.com
        variable_ringback: %(2000,4000,440,480)
        variable_transfer_ringback: %(400,200,400,450);%(400,2000,400,450)
        variable_hangup_after_bridge: true
        variable_continue_on_fail: true
        variable_webitel_record_file_name: d3463081-212b-4d54-b93d-63720cc9d665_recordSession.mp3
        variable_RECORD_MIN_SEC: 2
        variable_RECORD_STEREO: true
        variable_RECORD_BRIDGE_REQ: true
        variable_recording_follow_transfer: true
        variable_record_post_process_exec_api: luarun:RecordUpload.lua d3463081-212b-4d54-b93d-63720cc9d665 demo.webitel.com mp3 none recordSession
        variable_local_media_ip: 194.44.1.1
        variable_local_media_port: 19500
        variable_advertised_media_ip: 194.44.1.1
        variable_rtp_use_timer_name: soft
        variable_rtp_use_pt: 0
        variable_rtp_use_ssrc: 730683183
        variable_current_loop: 1
        variable_total_loops: 1
        variable_current_application_data: {domain_name=demo.webitel.com}user/100@demo.webitel.com
        variable_current_application: bridge
        variable_dialed_user: 100
        variable_dialed_domain: demo.webitel.com
        variable_originated_legs: ARRAY::1f4a8f90-d9b9-4699-a645-eb562d98b627;Outbound Call;100|:1f4a8f90-d9b9-4699-a645-eb562d98b627;Outbound Call;100
        variable_read_codec: PCMU
        variable_read_rate: 8000
        variable_endpoint_disposition: ANSWER
        variable_originate_causes: ARRAY::1f4a8f90-d9b9-4699-a645-eb562d98b627;NONE|:1f4a8f90-d9b9-4699-a645-eb562d98b627;NONE
        variable_originate_disposition: SUCCESS
        variable_DIALSTATUS: SUCCESS
        variable_last_bridge_to: 1f4a8f90-d9b9-4699-a645-eb562d98b627
        variable_bridge_channel: sofia/internal/100@10.10.10.101:5064
        variable_bridge_uuid: 1f4a8f90-d9b9-4699-a645-eb562d98b627
        variable_signal_bond: 1f4a8f90-d9b9-4699-a645-eb562d98b627
        variable_sip_to_tag: FF2vX9yD4947S
        variable_sip_from_tag: 3298371467
        variable_sip_cseq: 2
        variable_sip_call_id: 544689405@10.10.10.107
        variable_sip_full_via: SIP/2.0/UDP 10.10.10.107:5062;branch=z9hG4bK3871199108
        variable_sip_from_display: Igor
        variable_sip_full_from: "Igor" <sip:9999@demo.webitel.com:5070>;tag=3298371467
        variable_sip_full_to: <sip:100@demo.webitel.com:5070>;tag=FF2vX9yD4947S
        variable_last_sent_callee_id_name: Outbound Call
        variable_last_sent_callee_id_number: 100
        variable_switch_r_sdp: v=0
        o=- 20106 20107 IN IP4 10.10.10.107
        s=SDP data
        c=IN IP4 10.10.10.107
        t=0 0
        a=sendrecv
        m=audio 11792 RTP/AVP 0 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20

        variable_remote_media_ip: 10.10.10.107
        variable_remote_media_port: 11792
        variable_rtp_audio_recv_pt: 0
        variable_dtmf_type: rfc2833
        variable_rtp_2833_send_payload: 101
        variable_rtp_2833_recv_payload: 101
        variable_rtp_local_sdp_str: v=0
        o=webitel 1468553555 1468553558 IN IP4 194.44.1.1
        s=webitel
        c=IN IP4 194.44.1.1
        t=0 0
        m=audio 19500 RTP/AVP 0 101
        a=rtpmap:0 PCMU/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-16
        a=ptime:20
        a=sendrecv

        variable_switch_m_sdp: v=0
        o=- 20133 20134 IN IP4 10.10.10.101
        s=SDP data
        c=IN IP4 10.10.10.101
        t=0 0
        m=audio 11790 RTP/AVP 9 101
        a=rtpmap:9 G722/8000
        a=rtpmap:101 telephone-event/8000
        a=fmtp:101 0-15
        a=ptime:20
        m=video 0 RTP/AVP 104

        variable_zrtp_secure_media_confirmed_audio: false
        variable_sip_hangup_phrase: OK
        variable_last_bridge_hangup_cause: NORMAL_CLEARING
        variable_last_bridge_proto_specific_hangup_cause: sip:200
        variable_bridge_hangup_cause: NORMAL_CLEARING
