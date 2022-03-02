ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app bench https://github.com/DuckyThePilot/bench develop && \
  install_app wiki https://github.com/DuckyThePilot/wiki develop && \
  install_app chat https://github.com/DuckyThePilot/chat develop && \
  install_app frappe_tinymce https://github.com/DuckyThePilot/frappe_tinymce develop
