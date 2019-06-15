# DotNetCoreEntityFrameWorkCoreWebApp

Using Visual Studio 2017, might need Sql Server Database Tools installed in Visual Studio

1. Create a new Project
    -File > New >Project...> Visual C# > .Net Core > ASP.NET Core Web Application 
2. ASP.NET Core 2.2 > Web Application (Model-View-Controller) 
    -When trying install the EntityFrameworkCore Nuget Package and dependencies I was having a lot of trouble. People online said to install the [.NET CORE 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2#sdk-2.2.107) and that fixed my issues with installing Nuget Packages
    - Version 2.2.107 seems to be the last sdk version that can be used by vs2017. When you go to download an sdk, there may be a small disclaimer letting you know this is the case.
3. Include the "microsoft.entityframeworkcore" nuget package to your project
4. Create a database on the (localdb\MSSQLLocalDb) server
    1. Visual Studio Menu Bar > View > SQL Server Object Explorer
    2. A Pane titled "SQL Server Object Explorer" should appear
    3. SQl Server > (localdb)\MSSQLLocalDB > *Right Click* Databases > Add New Database 
        1. Database Name: EntityFrameworkCoreDatabase
        2. Database Location leave the default
        3. Click "OK"
    4. EntityFrameWorkCoreDatabase > *Right Click* Tables > Add New Table...
        1. Add a row with "name" in the **Name** column, **Data Type** varchar(50)
        2. Add a row with "age" in the **Name** column, **Data Type** nchar(10)
        3. Click the **Update** button with an arrow pointing up 
        4. A window should pop up titled "Preview Database Updates" > *Click* **Update Database**
5. You should now have a database with some table created for EntityFrameWorkCore to do its magic
6. Now we want to have EntityFrameWorkCore generate the classes from our tables in the database
    1. Visual Studio Menu Bar > Tools > NuGet Package Manager > Package Manager Console
    2. A pane should show up towards the bottom of the screen titled "Package Manager Console"
    3. In the console copy and paste the following string without the quotation marks:
    "Scaffold-DbContext "Server=(localdb)\mssqllocaldb;Database=EntityFrameWorkCoreDatabase;Trusted_Connection=True;" Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models"
        - If you choose a different server or database name, fix them in the previous string before running
    4. Now you should have 2 classes generated for you in the **Models** folder in your project
        - EntityFrameWorkCoreDatabaseContext.s
        - Table.cs
7. 
