* using Gradle >= 4.5 (does work in Gradle 4.4)
* running ./gradlew -S publish **succeeds**
* running ./gradlew -S -t publish **fails** with stacktrace:

```
$ ./gradlew publish -S -t                                                                                                                                                      
Continuous build is an incubating feature.                                                                                                                                     
                                                                                                                                                                               
FAILURE: Build failed with an exception.                                                                                                                                       
                                                                                                                                                                               
* What went wrong:                                                                                                                                                             
path may not be null or empty string. path='null'                                                                                                                              
                                                                                                                                                                               
* Try:                                                                                                                                                                         
Run with --info or --debug option to get more log output. Run with --scan to get full insights.                                                                                
                                                                                                                                                                               
* Exception is:                                                                                                                                                                
java.lang.IllegalArgumentException: path may not be null or empty string. path='null'                                                                                          
        at org.gradle.api.internal.file.AbstractBaseDirFileResolver.doResolve(AbstractBaseDirFileResolver.java:65)                                                             
        at org.gradle.api.internal.file.AbstractFileResolver.resolve(AbstractFileResolver.java:85)                                                                             
        at org.gradle.api.internal.file.AbstractFileResolver.resolve(AbstractFileResolver.java:67)                                                                             
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext$FileCollectionConverter.convertInto(DefaultFileCollectionResolveContext.java:188)      
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext.doResolve(DefaultFileCollectionResolveContext.java:143)                                
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext.resolveAsFileCollections(DefaultFileCollectionResolveContext.java:95)                  
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext$FileCollectionConverter.convertInto(DefaultFileCollectionResolveContext.java:172)      
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext.doResolve(DefaultFileCollectionResolveContext.java:112)                                
        at org.gradle.api.internal.file.collections.DefaultFileCollectionResolveContext.resolveAsFileCollections(DefaultFileCollectionResolveContext.java:95)                  
        at org.gradle.api.internal.file.CompositeFileCollection.getSourceCollections(CompositeFileCollection.java:172)                                                         
        at org.gradle.api.internal.file.CompositeFileCollection.registerWatchPoints(CompositeFileCollection.java:177)                                                          
        at org.gradle.api.execution.internal.DefaultTaskInputsListener.onExecute(DefaultTaskInputsListener.java:31)                                                            
        at org.gradle.api.internal.tasks.execution.SkipEmptySourceFilesTaskExecuter.execute(SkipEmptySourceFilesTaskExecuter.java:99)                                          
        at org.gradle.api.internal.tasks.execution.FinalizeInputFilePropertiesTaskExecuter.execute(FinalizeInputFilePropertiesTaskExecuter.java:44)                            
        at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:91)                                                    
        at org.gradle.api.internal.tasks.execution.ResolveTaskArtifactStateTaskExecuter.execute(ResolveTaskArtifactStateTaskExecuter.java:62)                                  
        at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:59)                                                
        at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:54)                                                              
        at org.gradle.api.internal.tasks.execution.ExecuteAtMostOnceTaskExecuter.execute(ExecuteAtMostOnceTaskExecuter.java:43)                                                
        at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:34)                                                      
        at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker$1.run(DefaultTaskGraphExecuter.java:256)                                              
        at org.gradle.internal.progress.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:336)                             
        at org.gradle.internal.progress.DefaultBuildOperationExecutor$RunnableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:328)                             
        at org.gradle.internal.progress.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:199)                                                          
        at org.gradle.internal.progress.DefaultBuildOperationExecutor.run(DefaultBuildOperationExecutor.java:110)                                                              
        at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker.execute(DefaultTaskGraphExecuter.java:249)                                            
        at org.gradle.execution.taskgraph.DefaultTaskGraphExecuter$EventFiringTaskWorker.execute(DefaultTaskGraphExecuter.java:238)                                            
        at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor$TaskExecutorWorker.processTask(DefaultTaskPlanExecutor.java:123)                                             
        at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor$TaskExecutorWorker.access$200(DefaultTaskPlanExecutor.java:79)                                               
        at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor$TaskExecutorWorker$1.execute(DefaultTaskPlanExecutor.java:104)                                               
        at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor$TaskExecutorWorker$1.execute(DefaultTaskPlanExecutor.java:98)                                                
        at org.gradle.execution.taskgraph.DefaultTaskExecutionPlan.execute(DefaultTaskExecutionPlan.java:663)                                                                  
        at org.gradle.execution.taskgraph.DefaultTaskExecutionPlan.executeWithTask(DefaultTaskExecutionPlan.java:597)                                                          
        at org.gradle.execution.taskgraph.DefaultTaskPlanExecutor$TaskExecutorWorker.run(DefaultTaskPlanExecutor.java:98)                                                      
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:63)                                                              
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:46)                                                                               
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)                                                                                     
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)                                                                                     
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:55)                                                               
        at java.lang.Thread.run(Thread.java:745)                                                                                                                               
                                                                                                                                                                               
                                                                                                                                                                               
* Get more help at https://help.gradle.org                                                                                                                                     
                                                                                                                                                                               
BUILD FAILED in 0s                                                                                                                                                             
2 actionable tasks: 2 executed
```
