# 使用python進行Selenium Web Driver自動化流程

## Introduction

Selenium主要有兩種方式控制瀏覽器，分別是RC (Remote Controll) 和 Web Driver:
### Remote Control:
RC主要透過Selenium server對瀏覽器進行控制，必須下載Selenium server元件(請參閱README.md)
![SeleniumRC](https://lh5.googleusercontent.com/khRtpEs2Uywkz6eSGABIylHVuc7cE4x_1Yuvjc1xZp4J9y3hl6OF9_dCoKr9xFxLJyWpG4YTP1nD2oIzIuFSDye0ANIgt5RHNKnLLuRQwkvpHmgEOanQ8xH-ecD5IDW6lw)
### Web Driver:
Web Driver不像RC需要Selenium server元件，但需要針對不同browser下載相應的套件
![SeleniumWD](https://lh4.googleusercontent.com/0Mftx44rTmuefHaRzrrIsghjHrHA7HFZCyWh-vee8lBOVRaGl0aTNrNfushC8s4OsdzImb5WBysSt4piopNVO4cLQPiVdxkSD9CN2L66UNNsFa_TtnOLdspGPCPwN1ORLg)

For google chrome [Web Driver](https://chromedriver.googlecode.com/files/chromedriver_win_23.0.1240.0.zip)

## Installation

欲使用Web driver的方式連結網頁，首先請確認已經安裝相應的package，並確認有安裝python以及pip

### Instlation:
	# Install selenium:
	C:\Python27\Scripts\pip.exe install -U selenium

	# Install purl:
		# purl is a powerful url builder module for python
	C:\Python27\Scripts\pip.exe install purl
### Testing:

	from selenium import webdriver
	from selenium.webdriver.common.keys import Keys
	
	driver = webdriver.Firefox()
	driver.get("http://www.python.org")
	assert "Python" in driver.title
	elem = driver.find_element_by_name("q")
	elem.send_keys("pycon")
	elem.send_keys(Keys.RETURN)
	assert "No results found." not in driver.page_source
	driver.close()