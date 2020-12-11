---
# This basic template provides core metadata fields for Markdown articles on docs.superoffice.com.

# Mandatory fields.
title: service_log_files       # (Required) Very important for SEO. Intent in a unique string of 43-59 chars including spaces.
description: Service log files # (Required) Important for SEO. Recommended character length is 115-145 characters including spaces.
author: {github-id}             # Your GitHub alias.
keywords:
so.topic:                       # article, howto, reference, concept, guide

# Optional fields. Don't forget to remove # if you need a field.
so.envir: onsite            # cloud or onsite
# so.client:                    # online, web, win, pocket, or mobile
---

# Service log files

Logfiles from Customer Service are stored in C:\\SuperOffice\\Customer Service\\log unless you have installed it to a different path.

You may also view the warning log in your browser by by adding the action "dumpWarningLog" with a "date" parameter to your rms.exe/rms.fcgi. This will require sufficient rights in Customer Service, and only works on rms.exe/rms.fcgi and the date format you have to use is as follows: yyyy-mm-dd.

Example: `http://<your website>/scripts/rms.exe?action=dumpWarningLog&date=2016-03-05`

In addition to the logfiles generated by Customer Service, we also log information from SuperOffice NetServer, you may find the location of your NetServer installation by opening the config file stored in C:\\SuperOffice\\Customer Service and looking at the value after nsEndPoint:

`nsEndPoint = http://localhost/SuperOfficeNS/ServicesXX`

Customer Service uses [Remote web services][1] and it will have a SuperOffice Product Configurator similar to 8.web. With this Product configurator you may enable debug logging under [Diagnostics][2].

After upgrading to a newer version of SuperOffice, if you experience strange behavior you may need to flush caches. This is done under the debug menu available under `http://<your website>/scripts/ticket.exe?action=debug`

![x][3]

<!-- Referenced links -->
[1]: https://community.superoffice.com/en/technical/documentation/install-upgrade/web/netserver--web-services/
[2]: https://community.superoffice.com/en/technical/documentation/administration/config-ini/debugweb/
[3]: https://community.superoffice.com/contentassets/4f0b281f6f5e47deb34f60baaea5d10f/actiondebug.png