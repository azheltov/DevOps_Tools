# 1. Setup and Initialization
from selenium import webdriver
from selenium.webdriver.common.by import By

# Initialize WebDriver (replace 'path/to/driver' with the actual path)
driver = webdriver.Chrome(executable_path='path/to/chromedriver')

# Open a webpage
driver.get('https://example.com')


# 2. Basic Browser Commands
# Maximize browser window
driver.maximize_window()

# Refresh the page
driver.refresh()

# Navigate to another URL
driver.get('https://anotherexample.com')

# Go back and forward in browser history
driver.back()
driver.forward()

# Get the page title
title = driver.title

# Get the current URL
current_url = driver.current_url


# 3. Locating Elements
# Find element by ID
element = driver.find_element(By.ID, 'element_id')

# Find element by Name
element = driver.find_element(By.NAME, 'element_name')

# Find element by XPath
element = driver.find_element(By.XPATH, '//tag[@attribute="value"]')

# Find element by CSS Selector
element = driver.find_element(By.CSS_SELECTOR, 'css.selector')

# Find element by Link Text
element = driver.find_element(By.LINK_TEXT, 'Link Text')

# Find element by Partial Link Text
element = driver.find_element(By.PARTIAL_LINK_TEXT, 'Partial Text')

# Find element by Tag Name
element = driver.find_element(By.TAG_NAME, 'tagname')

# Find multiple elements (e.g., all links)
elements = driver.find_elements(By.TAG_NAME, 'a')


# 4. Interacting with Elements
# Click an element
element.click()

# Enter text into a text field
element.send_keys('text to input')

# Clear a text field
element.clear()

# Submit a form
element.submit()


# 5. Handling Dropdowns
from selenium.webdriver.support.ui import Select

# Locate the dropdown element
dropdown = Select(driver.find_element(By.ID, 'dropdown_id'))

# Select by visible text
dropdown.select_by_visible_text('Option Text')

# Select by value
dropdown.select_by_value('option_value')

# Select by index
dropdown.select_by_index(2)


# 6. Handling Alerts and Pop-ups
# Switch to alert and accept
alert = driver.switch_to.alert
alert.accept()

# Switch to alert and dismiss
alert.dismiss()

# Get text from alert
alert_text = alert.text


# 7. Handling Frames and Windows
# Switch to frame by name or ID
driver.switch_to.frame('frame_name')

# Switch to frame by index
driver.switch_to.frame(0)

# Switch to default content (exit the frame)
driver.switch_to.default_content()

# Switch to a new window/tab
driver.switch_to.window(driver.window_handles[1])


# 8. Waits
# Implicit Wait
driver.implicitly_wait(10)  # seconds

# Explicit Wait
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

element = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.ID, 'element_id'))
)


# 9. Scrolling
# Scroll to a specific element
element = driver.find_element(By.ID, 'element_id')
driver.execute_script("arguments[0].scrollIntoView();", element)

# Scroll to the bottom of the page
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")


# 10. Taking Screenshots
# Take a screenshot and save it
driver.save_screenshot('screenshot.png')


# 11. Closing Browser
# Close current window
driver.close()

# Quit the browser (closes all windows)
driver.quit()
