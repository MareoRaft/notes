## Runs

Mlflow with start_run block is NOT NECESSARY.  We may instead use:

    mlflow.start_run()
    mlflow.log_param("my", "param")
    mlflow.log_metric("score", 100)
    mlflow.end_run()

2. The run starts when (a) it hits mlflow.start_run() or (b) any mlflow action (such as log_param, log_metric, or log_model) is executed.

3. The time/duration of the run in the Experiment table corresponds to the elapsed time from start_run to end_run.

4. The run ends when (a) it hits mlflow.end_run() or (b) the script finishes or (c) when the with mlflow.start_run(): block ends.
