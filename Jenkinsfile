node {
  checkout scm

  stage 'Deploy application release'
  writeFile file: 'extras.json', text: "{'image_tag':'${IMAGE_TAG}','ecs_tasks':[${TASKS}]}"
  withEnv(["VAUL_PASSWORD=${VAULT_PASSWORD}"]) {
    sh 'ansible-playbook site.yml --vault-password-file vault.py -e "@extras.json"'
  }
}
