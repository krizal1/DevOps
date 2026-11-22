pipeline {
    agent any
    stages {
        stage('Подготовка окружения') {
            steps {
                echo 'Установка зависимостей и клонирование репозиториев...'
                dir('ansible') {
                    sh 'ansible-playbook -i hosts run_playbook.yml --tags deploy'
                }
            }
        }
        stage('Запуск приложений') {
            steps {
                echo 'Запуск контейнеров через Docker Compose...'
                dir('ansible') {
                    sh 'ansible-playbook -i hosts run_playbook.yml --tags up'
                }
            }
        }
    }
}
