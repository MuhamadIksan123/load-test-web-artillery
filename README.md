# Program testing steps load-test-web

## Step 1: Install Artillery

To install Artillery, use the following command:

```
npm install -g artillery
```

## Step 2: Configure the YAML File (airports.yml)

Open or create a YAML configuration file (e.g., "airports.yml") and customize it for the API you want to test. Here's an example configuration:

```
config:
  target: "https://airportgap-stress-test.dev-tester.com/api"
  phases:
    - duration: 60
      arrivalRate: 5
      rampTo: 25

scenarios:
  - name: "Get first page of airports"
    flow:
      - get:
          url: "/airports"
```
Make sure to replace the target value with the appropriate API URL.

## Step 3: Run the Test (Optional: to check whether the program is finished or not)

To run the test, use the following command:

```
artillery run airports.yml
```

## Step 4: Generate Testing Reports

After running the test using the artillery run airports.yml command, you can use the following command to generate testing reports in both JSON and HTML formats:

```
artillery run --output report.json airports.yml && artillery report --output report.html report.json
```
These are two commands combined:

- artillery run --output report.json airports.yml: This runs the test and produces a report in JSON format with the filename "report.json." This report will contain all the test results and metrics.

- artillery report --output report.html report.json: This generates an HTML report based on the previously generated JSON report. The HTML report will be saved as "report.html."

## Step 5: Open the HTML Report in a Browser

After generating the HTML report, open the report in your web browser to view the test results in more detail. You can do this by following these steps:

1. Open your web browser (such as Chrome, Firefox, or Safari).

2. Open the HTML report by double-clicking the "report.html" file or using the "Open File" command in your browser.

3. You will see the stress testing report displayed in your browser. The report will include graphs, tables, and statistics that detail the test results, including response times, failures, and other important information about your API's performance during the stress test.

By opening the HTML report in your browser, you can analyze the test results more thoroughly and understand how your API handles the tested load during the stress test.

## Note
The configuration provided is an artillery load or stress testing script used to assess the performance of an API. Here's an explanation of the configuration:

1. target: This is the URL of the API being tested. In this case, the tested API is located at "https://airportgap-stress-test.dev-tester.com/api."

2. phases: This section defines the testing phases to be executed. There is one phase in this configuration with the following details:

- duration: The duration of the testing phase in seconds. In this case, the phase will run for 60 seconds.
- arrivalRate: The rate at which new virtual users arrive every second during the phase. In this case, there will be 5 new virtual users arriving every second.
- rampTo: The number of virtual users that will gradually increase until reaching this number during the phase. In this case, the number of virtual users will increase from 5 to 25 over 60 seconds.
3. scenarios: This section defines the testing scenarios. In this configuration, there is only one scenario named "Get the first page of airports." This scenario performs only one action, which is making an HTTP GET request to the URL "/airports." This means that this scenario will test the "/airports" endpoint of the specified API.

Overall, this artillery configuration will execute a stress test on the API by sending GET requests to the "/airports" endpoint for a duration of 60 seconds. The number of virtual users will gradually increase from 5 to 25 during the test, with a rate of 5 new virtual users arriving every second. The main goal of this test is to measure the API's performance in handling a specific load and observe how it responds as the number of virtual users increases.
