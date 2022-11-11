---
description: Popular desktop environments have dropped the legacy concept of a SysTray. Here’s a list of newer, capable, cross-desktop APIs to use instead.

redirect_from:
  - app-indicator
  - appindicator
  - app-indicators
  - appindicators
  - indicators
  - status-icon
  - statusicon
  - status-icons
  - statusicons
  - systemtray
  - sys-tray
  - sys-trays
  - systrays
---

# [Is Linux About]({{ site.baseurl }}/) SysTray?

{% assign des = site.desktop-environments | sort: "title" %}

## No.

Popular desktop environments have dropped the legacy concept of a SysTray (system tray, notification area, status icons, app indicators, tray icons, etc.). However, there are many newer, more capable, and cross-desktop APIs that replace the functionality previously provided by these icons.

Here you can find a list of replacement APIs and see how well-supported they are.

### Additional Resources

- [“Growing Beyond the System Tray”](https://www.youtube.com/watch?v=fPFdV-Z69Lo) talk by Daniel Foré at Linux App Summit (2019)
- [“Developer Tips: Backgrounding & System Integration”](https://blog.elementary.io/developer-tips-backgrounding-system-integration/) by Cassidy James Blaede for elementary (2018)
- [“Status Icons and GNOME”](https://blogs.gnome.org/aday/2017/08/31/status-icons-and-gnome/) by Allan Day for GNOME (2017)
- [“Farewell to the notification area”](https://ubuntu.com/blog/notification-area) by Matthew Paul Thomas for Ubuntu (2010)

## I want to…

- [Convey sync status or provide actions related to cloud storage](#cloudproviders)
- [Provide quick access to my app's commonly used actions](#desktop-actions)
- [Convey progress for long-running tasks](#launcher-entry)
- [Display how many items need action (such as unread messages)](#launcher-entry)
- [Provide media player controls or now playing info](#mpris)
- [Alert the user that something has changed in my app](#notifications)
- [Inform the user that my app is accessing system functions in the background (like screen recording)](#portals)

## CloudProviders

If you want to communicate synchronization status or provide actions related to cloud storage devices, you can use the CloudProviders DBus API

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Status Icon</th>
        {% for de in des %}
          {% assign status = de.cloudproviders.status-icon %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.cloudproviders.status-icon-note %}
            {% assign note = de.cloudproviders.status-icon-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Actions</th>
        {% for de in des %}
          {% assign status = de.cloudproviders.actions %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.cloudproviders.actions-note %}
            {% assign note = de.cloudproviders.actions-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

## Desktop Actions

If you want to provide quick access to common actions, you can add them to your .desktop file

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Actions</th>
        {% for de in des %}
          {% assign status = de.desktop-actions.actions %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.desktop-actions.actions-note %}
            {% assign note = de.desktop-actions.actions-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Icons</th>
        {% for de in des %}
          {% assign status = de.desktop-actions.icons %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.desktop-actions.icons-note %}
            {% assign note = de.desktop-actions.icons-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

## Launcher Entry

If you want to communicate progress information for long-running background tasks or the number of items needing action in your app (such as tasks or messages) you can use the LauncherEntry DBus API

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Progress Bar</th>
        {% for de in des %}
          {% assign status = de.launcher-entry.progress-bar %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.launcher-entry.progress-bar-note %}
            {% assign note = de.launcher-entry.progress-bar-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Badge</th>
        {% for de in des %}
          {% assign status = de.launcher-entry.badge %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.launcher-entry.badge-note %}
            {% assign note = de.launcher-entry.badge-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

## MPRIS

If you want the user to be able to access media player controls for you app, you can listen to and supply information to MPRIS

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Media Info</th>
        {% for de in des %}
          {% assign status = de.mpris.media-info %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.mpris.media-info-note %}
            {% assign note = de.mpris.media-info-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Player Controls</th>
        {% for de in des %}
          {% assign status = de.mpris.player-controls %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.mpris.player-controls-note %}
            {% assign note = de.mpris.player-controls-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Album Art</th>
        {% for de in des %}
          {% assign status = de.mpris.album-art %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.mpris.album-art-note %}
            {% assign note = de.mpris.album-art-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

## Notifications

If you want to alert the user that something has changed in your app, you can send a notification bubble

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Bubbles</th>
        {% for de in des %}
          {% assign status = de.notifications.bubbles %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.bubbles-note %}
            {% assign note = de.notifications.bubbles-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Actions</th>
        {% for de in des %}
          {% assign status = de.notifications.actions %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.actions-note %}
            {% assign note = de.notifications.actions-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Notification Center</th>
        {% for de in des %}
          {% assign status = de.notifications.notification-center %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.notifications-center-note %}
            {% assign note = de.notifications.notifications-center-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Images</th>
        {% for de in des %}
          {% assign status = de.notifications.images %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.images-note %}
            {% assign note = de.notifications.images-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Replace</th>
        {% for de in des %}
          {% assign status = de.notifications.replace %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.replace-note %}
            {% assign note = de.notifications.replace-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Inline Reply</th>
        {% for de in des %}
          {% assign status = de.notifications.inline-reply %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.notifications.inline-reply %}
            {% assign note = de.notifications.inline-reply %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

## Portals

XDG Desktop Portals are sandbox-compatible DBus APIs for accessing system functions. Desktop environments can use these portals to request consent from users and provide an ongoing visual indication of portal usage.

### Location

The Location Portal is responsible for providing apps with the device's current physical location.

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Consent</th>
        {% for de in des %}
          {% assign status = de.portals.location-consent %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.portals.location-consent-note %}
            {% assign note = de.portals.location-consent-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Indication</th>
        {% for de in des %}
          {% assign status = de.portals.location-indication %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.portals.location-indication-note %}
            {% assign note = de.portals.location-indication-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

### Screencast/Recording

The Screencast Portal is responsible for providing apps with the display's or a window's visible content i.e. for recording, streaming, or remote viewing.

<div class="overflow-x">
  <table>
    <thead>
      <tr>
        <th></th>
        {% for de in des %}
          <th>{{ de.title }}</th>
        {% endfor %}
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Consent</th>
        {% for de in des %}
          {% assign status = de.portals.screencast-consent %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.portals.screenshot-consent-note %}
            {% assign note = de.portals.screencast-consent-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
      <tr>
        <th>Indication</th>
        {% for de in des %}
          {% assign status = de.portals.screencast-indication %}
          {% if status == true %}
            {% assign status = "✔️" %}
            {% assign note = "Implemented" %}
          {% elsif status == false %}
            {% assign status = "✖️" %}
            {% assign note = "Not implemented" %}
          {% elsif status == "planned" %}
            {% assign status = "📝️" %}
            {% assign note = "Planned" %}
          {% elsif status == "partial" %}
            {% assign status = "🛠️" %}
            {% assign note = "Partially implemented" %}
          {% elsif status == "unknown" %}
            {% assign status = "❓️" %}
            {% assign note = "Unknown" %}
          {% endif %}
          {% if de.portals.screenshot-indication-note %}
            {% assign note = de.portals.screencast-indication-note %}
          {% endif %}
          <td class="{{ status }}" title="{{ note }}">{{ status }}</td>
        {% endfor %}
      </tr>
    </tbody>
  </table>
</div>

