---
layout: ../../layouts/post.astro
title: "Unit vs. Integration Testing: A To-Do List Example Across Frameworks"
description: Discover how to effectively use unit and integration testing in your projects, with a focus on React, Ruby on Rails, and Django.
dateFormatted: Aug 25th, 2024
---

To make the concepts of unit testing and integration testing clearer, let’s see how they work with code examples in three popular frameworks: React, Ruby on Rails, and Django.

### React Testing

In React, we use **Jest** for unit testing and **React Testing Library** for integration testing.

**Unit Testing in React:** Here’s a simple function `addTask` that adds a task to a list:

```javascript
function addTask(task, taskList) {
    return [...taskList, task];
}

// Jest Unit Test
test('adds a task to the list', () => {
    const taskList = ['Buy milk'];
    const newTask = 'Walk the dog';
    const updatedList = addTask(newTask, taskList);
    expect(updatedList).toEqual(['Buy milk', 'Walk the dog']);
});
```

This test checks if `addTask` correctly adds a new task to the list.

**Integration Testing in React:** For integration testing, we check how components work together:

```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import ToDoApp from './ToDoApp';

test('adds a task when the button is clicked', () => {
    render(<ToDoApp />);
    
    const input = screen.getByPlaceholderText('Enter a task');
    fireEvent.change(input, { target: { value: 'Buy groceries' } });
    
    const button = screen.getByText('Add Task');
    fireEvent.click(button);
    
    expect(screen.getByText('Buy groceries')).toBeInTheDocument();
});
```

This test makes sure that entering a task and clicking the button adds it to the list on the screen.

### Ruby on Rails Testing

In Ruby on Rails, **RSpec** is used for both unit and integration testing.

**Unit Testing in Rails:** Here’s a model with an `add_task` method:

```ruby
class Task < ApplicationRecord
  def self.add_task(task_name, tasks)
    tasks << task_name
  end
end

# RSpec Unit Test
RSpec.describe Task, type: :model do
  it 'adds a task to the list' do
    tasks = ['Buy milk']
    new_task = 'Walk the dog'
    updated_tasks = Task.add_task(new_task, tasks)
    expect(updated_tasks).to include('Walk the dog')
  end
end
```

This test checks if the `add_task` method adds a new task to the list.

**Integration Testing in Rails:** To test user interactions:

```ruby
require 'rails_helper'

RSpec.describe 'Adding a task', type: :feature do
  it 'adds a task to the list when the form is submitted' do
    visit new_task_path
    
    fill_in 'Task', with: 'Buy groceries'
    click_button 'Add Task'
    
    expect(page).to have_content('Buy groceries')
  end
end
```

This test simulates a user filling out a form and checks if the new task appears on the page.

### Django Testing

Django uses its built-in testing tools, which extend Python’s **unittest** framework, for unit tests, and tools like **Selenium** or **pytest-django** for integration tests.

**Unit Testing in Django:** Here’s a class with an `add_task` method:

```python
class TaskList:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)
        return self.tasks

# Django Unit Test
from django.test import TestCase

class TaskListTest(TestCase):
    def test_add_task(self):
        task_list = TaskList()
        task_list.add_task('Buy milk')
        self.assertIn('Buy milk', task_list.tasks)
```

This test checks if the `add_task` method adds a task to the list.

**Integration Testing in Django:** To test form submissions:

```python
from django.test import TestCase
from django.urls import reverse

class AddTaskTest(TestCase):
    def test_add_task(self):
        response = self.client.post(reverse('add_task'), {'task': 'Buy groceries'})
        self.assertContains(response, 'Buy groceries')
```

This test checks if a task submitted through a form is displayed correctly on the page.

### Conclusion

Unit testing focuses on individual parts of the code to ensure they work correctly, while integration testing checks how these parts work together. By understanding these concepts through examples in React, Ruby on Rails, and Django, you can better grasp how to apply these tests in your projects.