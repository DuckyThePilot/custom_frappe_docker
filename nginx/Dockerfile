ARG FRAPPE_BRANCH=develop
FROM node:14-buster
ARG FRAPPE_BRANCH=develop

COPY install_frappe.sh /install_frappe
COPY install_erpnext.sh /install_erpnext
COPY install_app.sh /install_app
COPY prepare_production.sh /prepare_production

# Install frappe
RUN /install_frappe ${FRAPPE_BRANCH} && \
  # Install erpnext
  /install_erpnext && \
  # Install required apps with following command
  # /install_app <app_name> <repo> <app_branch>
  /install_app wiki https://github.com/DuckyThePilot/wiki develop && \
  /install_app chat https://github.com/DuckyThePilot/chat develop && \
  /install_app frappe_tinymce https://github.com/DuckyThePilot/frappe_tinymce develop && \
  /install_app school https://github.com/DuckyThePilot/school develop && \
  /install_app persona https://github.com/DuckyThePilot/persona develop && \
  
  # Cleanup for production
  /prepare_production

FROM frappe/erpnext-nginx:${FRAPPE_BRANCH}

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync

# Append list of installed to apps.txt
RUN echo -n "wiki\nchat\nfrappe_tinymce\nschool\npersona" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
