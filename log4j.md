initLogging during servetcontext initilization
---
```java
	private void initLogging(Properties props)
	throws Exception {
		URL url;
		String logConf = props.getProperty(LOG_CONF_PROP);
		if (StringUtils.isNotBlank(logConf)) {
			url = new File(logConf).toURI().toURL();
		} else {
			url = this.getClass().getResource(DEF_LOG_CONF);
		}

		String dataDir = props.getProperty(DATA_DIR_PROP);
		if (StringUtils.isBlank(dataDir)) {
			dataDir = ".";
		}

		String logDir = dataDir + File.separator + "logs";
		new File(logDir).mkdirs();
		System.setProperty("os_log_dir", logDir);

		BasicConfigurator.resetConfiguration();
		PropertyConfigurator.configure(url);
		logger.info("Initialised logging configuration from following file: " + url);
		if (url.getProtocol().equals("file")) {
			PropertyConfigurator.configureAndWatch(url.getFile());
		}
	}
 ```
