# starts-
Project developer

import datetime

class Task:
    def __init__(self, description, due_date):
        self.description = description
        self.due_date = due_date
        self.completed = False

    def mark_completed(self):
        self.completed = True

class Project:
    def __init__(self, name):
        self.name = name
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)

    def get_incomplete_tasks(self):
        incomplete_tasks = []
        for task in self.tasks:
            if not task.completed:
                incomplete_tasks.append(task)
        return incomplete_tasks

    def get_task_due_dates(self):
        task_due_dates = []
        for task in self.tasks:
            if not task.completed:
                task_due_dates.append(task.due_date)
        return task_due_dates

class ProjectManager:
    def __init__(self):
        self.projects = []

    def add_project(self, project):
        self.projects.append(project)

    def create_project(self, name):
        project = Project(name)
        self.projects.append(project)
        return project

    def create_task(self, project, description, due_date):
        task = Task(description, due_date)
        project.add_task(task)

    def mark_task_complete(self, task):
        task.mark_completed()

    def get_incomplete_tasks(self):
        incomplete_tasks = []
        for project in self.projects:
            incomplete_tasks.extend(project.get_incomplete_tasks())
        return incomplete_tasks

    def get_task_due_dates(self):
        task_due_dates = []
        for project in self.projects:
            task_due_dates.extend(project.get_task_due_dates())
        return task_due_dates
