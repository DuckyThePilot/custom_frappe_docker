ARG FRAPPE_BRANCH=develop
FROM frappe/erpnext-worker:${FRAPPE_BRANCH}

RUN install_app wiki https://github.com/DuckyThePilot/wiki develop && \
  install_app chat https://github.com/DuckyThePilot/chat develop && \
  install_app frappe_tinymce https://github.com/DuckyThePilot/frappe_tinymce develop && \
  install_app school https://github.com/DuckyThePilot/school develop && \
  install_app persona https://github.com/DuckyThePilot/persona develop
