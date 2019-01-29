---
title: Base de datos de ejemplo para OLTP en memoria | Microsoft Docs
ms.custom: ''
ms.date: 11/30/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: df347f9b-b950-4e3a-85f4-b9f21735eae3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ddbafb58662497dc2ee9c513aa206d826d5db8c1
ms.sourcegitcommit: 170c275ece5969ff0c8c413987c4f2062459db21
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54226702"
---
# <a name="sample-database-for-in-memory-oltp"></a><span data-ttu-id="e2a87-102">Base de datos de ejemplo para OLTP en memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-102">Sample Database for In-Memory OLTP</span></span>
    
## <a name="overview"></a><span data-ttu-id="e2a87-103">Información general</span><span class="sxs-lookup"><span data-stu-id="e2a87-103">Overview</span></span>  
 <span data-ttu-id="e2a87-104">Este ejemplo muestra la característica OLTP en memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-104">This sample showcases the In-Memory OLTP feature.</span></span> <span data-ttu-id="e2a87-105">Muestra tablas optimizadas para memoria y procedimientos almacenados compilados de forma nativa y se puede usar para mostrar las ventajas de rendimiento de OLTP en memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-105">It shows  memory-optimized tables and natively-compiled stored procedures, and can be used to demonstrate performance benefits of In-Memory OLTP.</span></span>  
  
 <span data-ttu-id="e2a87-107">El ejemplo migra 5 tablas de la base de datos AdventureWorks a tablas optimizadas para memoria e incluye una carga de trabajo de demostración para el procesamiento de pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-107">The sample migrates 5 tables in the AdventureWorks database to memory-optimized, and it includes a demo workload for sales order processing.</span></span> <span data-ttu-id="e2a87-108">Se puede usar esta carga de trabajo de demostración para ver la ventaja de rendimiento que supone emplear OLTP en memoria en el servidor.</span><span class="sxs-lookup"><span data-stu-id="e2a87-108">You can use this demo workload to see the performance benefit of using In-Memory OLTP on your server.</span></span>  
  
 <span data-ttu-id="e2a87-109">En la descripción del ejemplo se explican los compromisos realizados al migrar las tablas a OLTP en memoria para compensar las características que no se admiten (todavía) en las tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-109">In the description of the sample we discuss the tradeoffs that were made in migrating the tables to In-Memory OLTP to account for the features that are not (yet) supported for memory-optimized tables.</span></span>  
  
 <span data-ttu-id="e2a87-110">La documentación de este ejemplo está estructurada de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-110">The documentation of this sample is structured as follows:</span></span>  
  
-   <span data-ttu-id="e2a87-111">[Requisitos previos](#Prerequisites) para instalar el ejemplo y ejecutar la carga de trabajo de demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-111">[Prerequisites](#Prerequisites) for installing the sample and running the demo workload</span></span>  
  
-   <span data-ttu-id="e2a87-112">Instrucciones para [Instalar el ejemplo de In-Memory OLTP basado en AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span><span class="sxs-lookup"><span data-stu-id="e2a87-112">Instructions for [Installing the In-Memory OLTP sample based on AdventureWorks](#InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks)</span></span>  
  
-   <span data-ttu-id="e2a87-113">[Descripción de las tablas y los procedimientos de ejemplo](#Descriptionofthesampletablesandprocedures): contiene descripciones de las tablas y los procedimientos que el ejemplo de OLTP en memoria ha agregado a AdventureWorks, y aspectos que se deben tener en cuenta para migrar algunas de las tablas originales de AdventureWorks a tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-113">[Description of the sample tables and procedures](#Descriptionofthesampletablesandprocedures) - this includes descriptions of the tables and procedures added to AdventureWorks by the In-Memory OLTP sample, as well as considerations for migrating some of the original AdventureWorks tables to memory-optimized</span></span>  
  
-   <span data-ttu-id="e2a87-114">Instrucciones para realizar [Medidas de rendimiento con la carga de trabajo de demostración](#PerformanceMeasurementsusingtheDemoWorkload): contiene instrucciones para instalar y ejecutar ostress, una herramienta que se usa para controlar la carga de trabajo y para ejecutar la carga de trabajo de demostración propiamente dicha.</span><span class="sxs-lookup"><span data-stu-id="e2a87-114">Instructions for performing [Performance Measurements using the Demo Workload](#PerformanceMeasurementsusingtheDemoWorkload) - this includes instructions for installing and running ostress, a tool using for driving the workload, as well as running the demo workload itself</span></span>  
  
-   [<span data-ttu-id="e2a87-115">Uso de memoria y de espacio en disco del ejemplo</span><span class="sxs-lookup"><span data-stu-id="e2a87-115">Memory and Disk Space Utilization in the Sample</span></span>](#MemoryandDiskSpaceUtilizationintheSample)  
  
##  <a name="Prerequisites"></a> <span data-ttu-id="e2a87-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e2a87-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="e2a87-117">Para las pruebas de rendimiento, un servidor con unas especificaciones similares al entorno de producción.</span><span class="sxs-lookup"><span data-stu-id="e2a87-117">For performance testing, a server with specifications similar to your production environment.</span></span> <span data-ttu-id="e2a87-118">Para esta muestra concreta, debe haber al menos 16 GB de memoria disponible para SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2a87-118">For this particular sample you should have at least 16GB of memory available to SQL Server.</span></span> <span data-ttu-id="e2a87-119">Para obtener instrucciones generales de hardware para OLTP en memoria, vea la entrada de blog siguiente: [Consideraciones de hardware para OLTP en memoria en SQL Server 2014](blog-hardware-in-memory-oltp.md)</span><span class="sxs-lookup"><span data-stu-id="e2a87-119">For general guidelines on hardware for In-Memory OLTP, see the following blog post: [Hardware considerations for In-Memory OLTP in SQL Server 2014](blog-hardware-in-memory-oltp.md)</span></span>

##  <a name="InstallingtheIn-MemoryOLTPsamplebasedonAdventureWorks"></a> <span data-ttu-id="e2a87-120">Instalar el ejemplo de In-Memory OLTP basado en AdventureWorks</span><span class="sxs-lookup"><span data-stu-id="e2a87-120">Installing the In-Memory OLTP sample based on AdventureWorks</span></span>  
 <span data-ttu-id="e2a87-121">Siga estos pasos para instalar el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-121">Follow these steps to install the sample:</span></span>  
  
1.  <span data-ttu-id="e2a87-122">Descargue AdventureWorks2016CTP3.bak y SQLServer2016CTP3Samples.zip desde [https://www.microsoft.com/download/details.aspx?id=49502](https://www.microsoft.com/download/details.aspx?id=49502) en una carpeta local (por ejemplo, 'c:\temp').</span><span class="sxs-lookup"><span data-stu-id="e2a87-122">Download AdventureWorks2016CTP3.bak and SQLServer2016CTP3Samples.zip from: [https://www.microsoft.com/download/details.aspx?id=49502](https://www.microsoft.com/download/details.aspx?id=49502) to a local folder, for example 'c:\temp'.</span></span>  

  
    1.  <span data-ttu-id="e2a87-124">Identifique la carpeta de destino y el nombre del archivo de datos, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-124">Identify the target folder and filename for the data file, for example</span></span>  
  
         <span data-ttu-id="e2a87-125">'h:\DATA\AdventureWorks2016CTP3_Data.mdf'</span><span class="sxs-lookup"><span data-stu-id="e2a87-125">'h:\DATA\AdventureWorks2016CTP3_Data.mdf'</span></span>  
  
    2.  <span data-ttu-id="e2a87-126">Identifique la carpeta de destino y el nombre del archivo de registro, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-126">Identify the target folder and filename for the log file, for example</span></span>  
  
         <span data-ttu-id="e2a87-127">'i:\DATA\AdventureWorks2016CTP3_log.ldf'</span><span class="sxs-lookup"><span data-stu-id="e2a87-127">'i:\DATA\AdventureWorks2016CTP3_log.ldf'</span></span>  
  
        1.  <span data-ttu-id="e2a87-128">El archivo de registro debe colocarse en otra unidad diferente que el archivo de datos, idealmente en una unidad de baja latencia como un almacenamiento SSD o PCIe, para obtener el máximo rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e2a87-128">The log file should be placed on a different drive than the data file, ideally a low latency drive such as an SSD or PCIe storage, for maximum performance.</span></span>  
  
     <span data-ttu-id="e2a87-129">Script T-SQL de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-129">Example T-SQL script:</span></span>  
  
    ```  
    RESTORE DATABASE [AdventureWorks2016CTP3]   
      FROM DISK = N'C:\temp\AdventureWorks2016CTP3.bak'   
        WITH FILE = 1,    
      MOVE N'AdventureWorks2016_Data' TO N'h:\DATA\AdventureWorks2016CTP3_Data.mdf',    
      MOVE N'AdventureWorks2016_Log' TO N'i:\DATA\AdventureWorks2016CTP3_log.ldf',  
      MOVE N'AdventureWorks2016CTP3_mod' TO N'h:\data\AdventureWorks2016CTP3_mod'  
     GO  
    ```  
  
3.  <span data-ttu-id="e2a87-130">Para ver la carga de trabajo y scripts de ejemplo, descomprima el archivo SQLServer2016CTP3Samples.zip en una carpeta local.</span><span class="sxs-lookup"><span data-stu-id="e2a87-130">To view the sample scripts and workload, unpack the file SQLServer2016CTP3Samples.zip to a local folder.</span></span> <span data-ttu-id="e2a87-131">Para obtener instrucciones sobre cómo ejecutar la carga de trabajo, consulte el archivo In-Memory OLTP\readme.txt.</span><span class="sxs-lookup"><span data-stu-id="e2a87-131">Consult the file In-Memory OLTP\readme.txt  for instructions on running the workload.</span></span>  
  
##  <a name="Descriptionofthesampletablesandprocedures"></a> <span data-ttu-id="e2a87-132">Descripción de las tablas y los procedimientos de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-132">Description of the sample tables and procedures</span></span>  
 <span data-ttu-id="e2a87-133">El ejemplo crea nuevas tablas para productos y pedidos de venta basadas en tablas existentes en AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e2a87-133">The sample creates new tables for products and sales orders, based on existing tables in AdventureWorks.</span></span> <span data-ttu-id="e2a87-134">El esquema de las nuevas tablas es similar a las tablas existentes, con algunas diferencias, como se explica a continuación.</span><span class="sxs-lookup"><span data-stu-id="e2a87-134">The schema of the new tables is similar to the existing tables, with a few differences, as explained below.</span></span>  
  
 <span data-ttu-id="e2a87-135">Las nuevas tablas optimizadas para memoria llevan el sufijo "_inmem".</span><span class="sxs-lookup"><span data-stu-id="e2a87-135">The new memory-optimized tables carry the suffix '_inmem'.</span></span> <span data-ttu-id="e2a87-136">El ejemplo también incluye las tablas correspondientes que llevan el sufijo "_ondisk"; estas tablas se pueden usar para realizar una comparación uno a uno entre el rendimiento de las tablas optimizadas para memoria y las tablas basadas en disco del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-136">The sample also includes corresponding tables carrying the suffix '_ondisk' - these tables can be used to make a one-to-one comparison between the performance of memory-optimized tables and disk-based tables on your system..</span></span>  
  
 <span data-ttu-id="e2a87-137">Tenga en cuenta que las tablas optimizadas para memoria empleadas en la carga de trabajo para la comparación de rendimiento son totalmente durables y con registro completo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-137">Note that the memory-optimized tables used in the workload for performance comparison are fully durable and fully logged.</span></span> <span data-ttu-id="e2a87-138">No sacrifican la durabilidad o la confiabilidad para conseguir la mejora del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e2a87-138">They do not sacrifice durability or reliability to attain the performance gain.</span></span>  
  
 <span data-ttu-id="e2a87-139">La carga de trabajo de destino de este ejemplo es el procesamiento de pedidos de venta, donde también tenemos en cuenta la información sobre productos y descuentos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-139">The target workload for this sample is sales order processing, where we consider also information about products and discounts.</span></span> <span data-ttu-id="e2a87-140">Para eso se usan las tablas SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer y SpecialOfferProduct.</span><span class="sxs-lookup"><span data-stu-id="e2a87-140">To this end, the table SalesOrderHeader, SalesOrderDetail, Product, SpecialOffer, and SpecialOfferProduct.</span></span>  
  
 <span data-ttu-id="e2a87-141">Se emplean dos nuevos procedimientos almacenados, Sales.usp_InsertSalesOrder_inmem y Sales.usp_UpdateSalesOrderShipInfo_inmem, para insertar pedidos de venta y actualizar la información de envío de un pedido de venta determinado.</span><span class="sxs-lookup"><span data-stu-id="e2a87-141">Two new stored procedures, Sales.usp_InsertSalesOrder_inmem and Sales.usp_UpdateSalesOrderShipInfo_inmem, are used to insert sales orders and to update the shipping information of a given sales order.</span></span>  
  
 <span data-ttu-id="e2a87-142">El nuevo esquema 'Demo' contiene tablas del asistente y procedimientos almacenados para ejecutar una carga de trabajo de demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-142">The new schema 'Demo' contains helper tables and stored procedures to execute a demo workload.</span></span>  
  
 <span data-ttu-id="e2a87-143">En concreto, el ejemplo de OLTP en memoria agrega los siguientes objetos a AdventureWorks:</span><span class="sxs-lookup"><span data-stu-id="e2a87-143">Concretely, the In-Memory OLTP sample adds the following objects to AdventureWorks:</span></span>  
  
### <a name="tables-added-by-the-sample"></a><span data-ttu-id="e2a87-144">Tablas agregadas por el ejemplo</span><span class="sxs-lookup"><span data-stu-id="e2a87-144">Tables added by the sample</span></span>  
  
#### <a name="the-new-tables"></a><span data-ttu-id="e2a87-145">Las nuevas tablas</span><span class="sxs-lookup"><span data-stu-id="e2a87-145">The New Tables</span></span>  
 <span data-ttu-id="e2a87-146">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-146">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-147">Información de encabezado sobre los pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-147">Header information about sales orders.</span></span> <span data-ttu-id="e2a87-148">Cada pedido de venta tiene una fila en esta tabla.</span><span class="sxs-lookup"><span data-stu-id="e2a87-148">Each sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="e2a87-149">Sales.SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-149">Sales.SalesOrderDetail_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-150">Detalles de los pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-150">Details of sales orders.</span></span> <span data-ttu-id="e2a87-151">Cada artículo de un pedido de venta tiene una fila en esta tabla.</span><span class="sxs-lookup"><span data-stu-id="e2a87-151">Each line item of a sales order has one row in this table.</span></span>  
  
 <span data-ttu-id="e2a87-152">Sales.SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-152">Sales.SpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-153">Información sobre ofertas especiales, incluido el porcentaje de descuento asociado a cada oferta especial.</span><span class="sxs-lookup"><span data-stu-id="e2a87-153">Information about special offers, including the discount percentage associated with each special offer.</span></span>  
  
 <span data-ttu-id="e2a87-154">Sales.SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-154">Sales.SpecialOfferProduct_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-155">Tabla de referencia entre las ofertas especiales y los productos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-155">Reference table between special offers and products.</span></span> <span data-ttu-id="e2a87-156">Cada oferta especial puede abarcar cero o más productos, y cada producto puede estar incluido en cero o más ofertas especiales.</span><span class="sxs-lookup"><span data-stu-id="e2a87-156">Each special offer can feature zero or more products, and each product can be featured in zero or more special offers.</span></span>  
  
 <span data-ttu-id="e2a87-157">Production.Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-157">Production.Product_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-158">Información sobre productos, incluido el precio de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-158">Information about products, including their list price.</span></span>  
  
 <span data-ttu-id="e2a87-159">Demo.DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e2a87-159">Demo.DemoSalesOrderDetailSeed</span></span>  
  
-   <span data-ttu-id="e2a87-160">Se usa en la carga de trabajo de demostración para generar pedidos de venta de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-160">Used in the demo workload to construct sample sales orders.</span></span>  
  
 <span data-ttu-id="e2a87-161">Variaciones basadas en disco de las tablas:</span><span class="sxs-lookup"><span data-stu-id="e2a87-161">Disk-based variations of the tables:</span></span>  
  
-   <span data-ttu-id="e2a87-162">Sales.SalesOrderHeader_ondisk</span><span class="sxs-lookup"><span data-stu-id="e2a87-162">Sales.SalesOrderHeader_ondisk</span></span>  
  
-   <span data-ttu-id="e2a87-163">Sales.SalesOrderDetail_ondisk</span><span class="sxs-lookup"><span data-stu-id="e2a87-163">Sales.SalesOrderDetail_ondisk</span></span>  
  
-   <span data-ttu-id="e2a87-164">Sales.SpecialOffer_ondisk</span><span class="sxs-lookup"><span data-stu-id="e2a87-164">Sales.SpecialOffer_ondisk</span></span>  
  
-   <span data-ttu-id="e2a87-165">Sales.SpecialOfferProduct_ondisk</span><span class="sxs-lookup"><span data-stu-id="e2a87-165">Sales.SpecialOfferProduct_ondisk</span></span>  
  
-   <span data-ttu-id="e2a87-166">Production.Product_ondisk</span><span class="sxs-lookup"><span data-stu-id="e2a87-166">Production.Product_ondisk</span></span>  
  
#### <a name="differences-between-original-disk-based-and-the-and-new-memory-optimized-tables"></a><span data-ttu-id="e2a87-167">Diferencias entre las tablas originales basadas en disco y las nuevas tablas optimizadas para memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-167">Differences between original disk-based and the and new memory-optimized tables</span></span>  
 <span data-ttu-id="e2a87-168">En general, las nuevas tablas de este ejemplo emplean las mismas columnas y los mismos tipos de datos que las tablas originales.</span><span class="sxs-lookup"><span data-stu-id="e2a87-168">For the most part, the new tables introduced by this sample use the same columns and the same data types as the original tables.</span></span> <span data-ttu-id="e2a87-169">Sin embargo, hay algunas diferencias.</span><span class="sxs-lookup"><span data-stu-id="e2a87-169">However, there are a few differences.</span></span> <span data-ttu-id="e2a87-170">A continuación se enumeran las diferencias y el motivo de los cambios.</span><span class="sxs-lookup"><span data-stu-id="e2a87-170">We list the differences below, along with a rationale for the changes.</span></span>  
  
 <span data-ttu-id="e2a87-171">Sales.SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-171">Sales.SalesOrderHeader_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-172">Las*restricciones DEFAULT* se admiten en las tablas optimizadas para memoria y la mayoría de las restricciones DEFAULT se migran tal cual.</span><span class="sxs-lookup"><span data-stu-id="e2a87-172">*Default constraints* are supported for memory-optimized tables, and most default constraints we migrated as is.</span></span> <span data-ttu-id="e2a87-173">Sin embargo, la tabla original Sales.SalesOrderHeader contiene dos restricciones DEFAULT que recuperan la fecha actual, para las columnas OrderDate y ModifiedDate.</span><span class="sxs-lookup"><span data-stu-id="e2a87-173">However, the original table Sales.SalesOrderHeader contains two default constraints that retrieve the current date, for the columns OrderDate and ModifiedDate.</span></span> <span data-ttu-id="e2a87-174">En una carga de trabajo de procesamiento de pedidos de alto rendimiento con mucha simultaneidad, cualquier recurso global puede convertirse en un punto de contención.</span><span class="sxs-lookup"><span data-stu-id="e2a87-174">In a high throughput order processing workload with a lot of concurrency, any global resource can become a point of contention.</span></span> <span data-ttu-id="e2a87-175">La hora del sistema es un recurso global y hemos observado que puede convertirse en un cuello de botella cuando se ejecuta una carga de trabajo de OLTP en memoria que inserta pedidos de venta, especialmente si es necesario recuperar la hora del sistema para varias columnas en el encabezado del pedido de venta, así como los detalles del pedido de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-175">System time is such a global resource, and we have observed that it can become a bottleneck when running an In-Memory OLTP workload that inserts sales orders, in particular if the system time needs to be retrieved for multiple columns in the sales order header, as well as the sales order details.</span></span> <span data-ttu-id="e2a87-176">Para resolver el problema en este ejemplo se recupera la hora del sistema solo una vez para cada pedido de venta que se inserta, y se usa ese valores para las columnas datetime de SalesOrderHeader_inmem y SalesOrderDetail_inmem, en el procedimiento almacenado Sales.usp_InsertSalesOrder_inmem.</span><span class="sxs-lookup"><span data-stu-id="e2a87-176">The problem is addressed in this sample by retrieving the system time only once for each sales order that is inserted, and use that value for the datetime columns in SalesOrderHeader_inmem and SalesOrderDetail_inmem, in the stored procedure Sales.usp_InsertSalesOrder_inmem.</span></span>  
  
-   <span data-ttu-id="e2a87-177">*UDT de alias:* la tabla original usa dos tipos de datos definidos por el usuario (UDT) de alias, dbo.OrderNumber y dbo.AccountNumber, para las columnas PurchaseOrderNumber y AccountNumber, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-177">*Alias UDTs* - The original table uses two alias user-defined data types (UDTs) dbo.OrderNumber and dbo.AccountNumber, for the columns PurchaseOrderNumber and AccountNumber, respectively.</span></span><span data-ttu-id="e2a87-178">no admite UDT de alias para las tablas optimizadas para memoria, por lo que las tablas nuevas usan los tipos de datos del sistema nvarchar(25) y nvarchar(15), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-178">does not support alias UDT for memory-optimized tables, thus the new tables use system data types nvarchar(25) and nvarchar(15), respectively.</span></span>  
  
-   <span data-ttu-id="e2a87-179">*Columnas que aceptan valores NULL en claves de índice:* en la tabla original, la columna SalesPersonID acepta valores NULL, mientras que en las tablas nuevas esa columna no acepta valores NULL y tiene una restricción DEFAULT con el valor (-1).</span><span class="sxs-lookup"><span data-stu-id="e2a87-179">*Nullable columns in index keys* - In the original table, the column SalesPersonID is nullable, while in the new tables the column is not nullable and has a default constraint with value (-1).</span></span> <span data-ttu-id="e2a87-180">Esto se debe a que los índices de las tablas optimizadas para memoria no pueden tener columnas que aceptan valores NULL en la clave de índice; -1 es un suplente para NULL en este caso.</span><span class="sxs-lookup"><span data-stu-id="e2a87-180">This is because indexes on memory-optimized tables cannot have nullable columns in the index key; -1 is a surrogate for NULL in this case.</span></span>  
  
-   <span data-ttu-id="e2a87-181">*Columnas calculadas:* se omiten las columnas calculadas SalesOrderNumber y TotalDue, ya que  no admite columnas calculadas en tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-181">*Computed columns* - The computed columns SalesOrderNumber and TotalDue are omitted, as does not support computed columns in memory-optimized tables.</span></span> <span data-ttu-id="e2a87-182">La nueva vista Sales.vSalesOrderHeader_extended_inmem refleja las columnas SalesOrderNumber y TotalDue.</span><span class="sxs-lookup"><span data-stu-id="e2a87-182">The new view Sales.vSalesOrderHeader_extended_inmem reflects the columns SalesOrderNumber and TotalDue.</span></span> <span data-ttu-id="e2a87-183">Por tanto, puede usar esta vista si se necesitan estas columnas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-183">Therefore, you can use this view if these columns are needed.</span></span>  

    - <span data-ttu-id="e2a87-184">**Se aplica a:**  CTP 1.1.</span><span class="sxs-lookup"><span data-stu-id="e2a87-184">**Applies to:** .</span></span>  
<span data-ttu-id="e2a87-185">A partir de  CTP 1.1, se admiten columnas calculadas en tablas e índices optimizados para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-185">Beginning with CTP 1.1, computed columns are supported in memory-optimized tables and indexes.</span></span>

  
-   <span data-ttu-id="e2a87-186">Las*restricciones FOREIGN KEY* se admiten para tablas optimizadas para memoria en , pero solo si las tablas de referencia también están optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-186">*Foreign key constraints* are supported for memory-optimized tables in ssSQL15](../../includes/sssql15-md.md)], but only if the referenced tables are also memory-optimized.</span></span> <span data-ttu-id="e2a87-187">Las claves externas que hagan referencia a tablas de referencia que también se migran a tablas optimizadas para memoria se conservan en esas tablas migradas, mientras que otras claves externas se omiten.</span><span class="sxs-lookup"><span data-stu-id="e2a87-187">Foreign keys that reference tables that are also migrated to memory-optimized are kept in the migrated tables, while other foreign keys are omitted.</span></span>  <span data-ttu-id="e2a87-188">Además, SalesOrderHeader_inmem es una tabla sin interrupción en la carga de trabajo de ejemplo, y las restricciones de clave externa requieren un procesamiento adicional para todas las operaciones DML, ya que tienen que hacer búsquedas en todas las demás tablas a las que se hace referencia en estas restricciones.</span><span class="sxs-lookup"><span data-stu-id="e2a87-188">In addition, SalesOrderHeader_inmem is a hot table in the example workload, and foreign keys constraints require additional processing for all DML operations, as it requires lookups in all the other tables referenced in these constraints.</span></span> <span data-ttu-id="e2a87-189">Por tanto, la suposición es que la aplicación garantiza la integridad referencial de la tabla Sales.SalesOrderHeader_inmem, y la integridad referencial no se valida cuando se insertan filas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-189">Therefore, the assumption is that the app ensures referential integrity for the Sales.SalesOrderHeader_inmem table, and referential integrity is not validated when rows are inserted.</span></span>  
  
-   <span data-ttu-id="e2a87-190">*Rowguid:* la columna rowguid se omite.</span><span class="sxs-lookup"><span data-stu-id="e2a87-190">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e2a87-191">Aunque se admite uniqueidentifier en las tablas optimizadas para memoria, la opción ROWGUIDCOL no se admite en ssSQL15](../../includes/sssql15-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2a87-191">While uniqueidentifier is support for memory-optimized tables, the option ROWGUIDCOL is not supported in ssSQL15](../../includes/sssql15-md.md)].</span></span> <span data-ttu-id="e2a87-192">Las columnas de esta clase se suelen usar para la replicación de mezcla o para tablas que incluyen columnas FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="e2a87-192">Columns of this kind are typically used for either merge replication or tables that have filestream columns.</span></span> <span data-ttu-id="e2a87-193">En este ejemplo no se incluye ninguna de ellas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-193">This sample includes neither.</span></span>  
  
 <span data-ttu-id="e2a87-194">Sales.SalesOrderDetail</span><span class="sxs-lookup"><span data-stu-id="e2a87-194">Sales.SalesOrderDetail</span></span>  
  
-   <span data-ttu-id="e2a87-195">*Restricciones DEFAULT*: igual que en SalesOrderHeader, la restricción DEFAULT que requiere la fecha y la hora del sistema no se migra; en su lugar, el procedimiento almacenado que inserta pedidos de venta se encarga de insertar la fecha y la hora actuales del sistema en la primera inserción.</span><span class="sxs-lookup"><span data-stu-id="e2a87-195">*Default constraints* - similar to SalesOrderHeader, the default constraint requiring the system date/time is not migrated, instead the stored procedure inserting sales orders takes care of inserting the current system date/time on first insert.</span></span>  
  
-   <span data-ttu-id="e2a87-196">*Columnas calculadas*: la columna calculada LineTotal no se ha migrado, ya que en ssSQL15](../../includes/sssql15-md.md)] no se admiten columnas calculadas en las tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-196">*Computed columns* - the computed column LineTotal was not migrated as computed columns are not supported with memory-optimized tables in ssSQL15](../../includes/sssql15-md.md)].</span></span> <span data-ttu-id="e2a87-197">Para obtener acceso a esta columna, use la vista Sales.vSalesOrderDetail_extended_inmem.</span><span class="sxs-lookup"><span data-stu-id="e2a87-197">To access this column use the view Sales.vSalesOrderDetail_extended_inmem.</span></span>  
  
-   <span data-ttu-id="e2a87-198">*Rowguid:* la columna rowguid se omite.</span><span class="sxs-lookup"><span data-stu-id="e2a87-198">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e2a87-199">Para obtener detalles, vea la descripción de la tabla SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="e2a87-199">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="e2a87-200">Production.Product</span><span class="sxs-lookup"><span data-stu-id="e2a87-200">Production.Product</span></span>  
  
-   <span data-ttu-id="e2a87-201">*UDT de alias*: en la tabla original se usa el tipo de datos definido por el usuario dbo.Flag, que equivale al tipo de datos del sistema bit.</span><span class="sxs-lookup"><span data-stu-id="e2a87-201">*Alias UDTs* - the original table uses the user-defined data type dbo.Flag, which is equivalent to the system data type bit.</span></span> <span data-ttu-id="e2a87-202">La tabla migrada usa el tipo de datos bit en su lugar.</span><span class="sxs-lookup"><span data-stu-id="e2a87-202">The migrated table uses the bit data type instead.</span></span>  
  
-   <span data-ttu-id="e2a87-203">*Rowguid:* la columna rowguid se omite.</span><span class="sxs-lookup"><span data-stu-id="e2a87-203">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e2a87-204">Para obtener detalles, vea la descripción de la tabla SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="e2a87-204">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="e2a87-205">Sales.SpecialOffer</span><span class="sxs-lookup"><span data-stu-id="e2a87-205">Sales.SpecialOffer</span></span>  
  
-   <span data-ttu-id="e2a87-206">*Rowguid:* la columna rowguid se omite.</span><span class="sxs-lookup"><span data-stu-id="e2a87-206">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e2a87-207">Para obtener detalles, vea la descripción de la tabla SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="e2a87-207">For details see the description for the table SalesOrderHeader.</span></span>  
  
 <span data-ttu-id="e2a87-208">Sales.SpecialOfferProduct</span><span class="sxs-lookup"><span data-stu-id="e2a87-208">Sales.SpecialOfferProduct</span></span>  
  
-   <span data-ttu-id="e2a87-209">*Rowguid:* la columna rowguid se omite.</span><span class="sxs-lookup"><span data-stu-id="e2a87-209">*Rowguid* - The rowguid column is omitted.</span></span> <span data-ttu-id="e2a87-210">Para obtener detalles, vea la descripción de la tabla SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="e2a87-210">For details see the description for the table SalesOrderHeader.</span></span>  
  
#### <a name="considerations-for-indexes-on-memory-optimized-tables"></a><span data-ttu-id="e2a87-211">Consideraciones sobre los índices de tablas optimizadas para memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-211">Considerations for indexes on memory-optimized tables</span></span>  
 <span data-ttu-id="e2a87-212">El índice de línea base para las tablas optimizadas para memoria es el índice no clúster, que admite búsquedas de puntos (búsqueda de índice en predicado de igualdad), recorridos de intervalo (búsqueda de índice en predicados de desigualdad), exámenes de índice completos y exámenes ordenados.</span><span class="sxs-lookup"><span data-stu-id="e2a87-212">The baseline index for memory-optimized tables is the NONCLUSTERED index, which supports point lookups (index seek on equality predicate), range scans (index seek in inequality predicate), full index scans, and ordered scans.</span></span> <span data-ttu-id="e2a87-213">Además, los índices no clúster admiten búsquedas en las columnas iniciales de la clave de índice.</span><span class="sxs-lookup"><span data-stu-id="e2a87-213">In addition, NONCLUSTERED indexes support searching on leading columns of the index key.</span></span> <span data-ttu-id="e2a87-214">De hecho, los índices no clúster optimizados para memoria admiten todas las operaciones compatibles con los índices no clúster basados en disco, con la única excepción de los exámenes hacia atrás.</span><span class="sxs-lookup"><span data-stu-id="e2a87-214">In fact memory-optimized NONCLUSTERED indexes support all the operations supported by disk-based NONCLUSTERED indexes, with the only exception being backward scans.</span></span> <span data-ttu-id="e2a87-215">Por tanto, el uso de índices no clúster es una opción segura para los índices.</span><span class="sxs-lookup"><span data-stu-id="e2a87-215">Therefore, using NONCLUSTERED indexes is a safe choice for your indexes.</span></span>  
  
 <span data-ttu-id="e2a87-216">Se pueden usar índices hash para optimizar aún más la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-216">HASH indexes are can be used to further optimize the workload.</span></span> <span data-ttu-id="e2a87-217">Están optimizados especialmente para las búsquedas de puntos y las inserciones de filas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-217">They are particularly optimized for point lookups and row inserts.</span></span> <span data-ttu-id="e2a87-218">Sin embargo, hay que tener en cuenta que no admiten recorridos de intervalo, exámenes ordenados ni búsquedas en columnas de clave de índice iniciales.</span><span class="sxs-lookup"><span data-stu-id="e2a87-218">However, one must consider that they do not support range scans, ordered scans, or search on leading index key columns.</span></span> <span data-ttu-id="e2a87-219">Por tanto, hay que tener cuidado cuando se usen estos índices.</span><span class="sxs-lookup"><span data-stu-id="e2a87-219">Therefore, care needs to be taken when using these indexes.</span></span> <span data-ttu-id="e2a87-220">Además, es necesario especificar el bucket_count en el momento de la creación.</span><span class="sxs-lookup"><span data-stu-id="e2a87-220">In addition, it is necessary to specify the bucket_count at create time.</span></span> <span data-ttu-id="e2a87-221">Normalmente se debe establecer entre una y dos veces el número de valores de clave de índice, pero la sobrestimación no suele suponer ningún problema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-221">It should usually be set at between one and two times the number of index key values, but overestimating is usually not a problem.</span></span>  
  
 <span data-ttu-id="e2a87-222">Vea los Libros en pantalla para obtener más información sobre las [directrices para usar índices](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) y las directrices para [elegir el número correcto de depósitos](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span><span class="sxs-lookup"><span data-stu-id="e2a87-222">See Books Online for more details about [index guidelines](https://technet.microsoft.com/library/dn133166\(v=sql.120\).aspx) and guidelines for [choosing the right bucket_count](https://technet.microsoft.com/library/dn494956\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="e2a87-223">Los índices de las tablas migradas se han optimizado para la carga de trabajo de procesamiento de pedidos de venta de demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-223">The indexes on the migrated tables have been tuned for the demo sales order processing workload.</span></span> <span data-ttu-id="e2a87-224">La carga de trabajo usa inserciones y búsquedas de puntos en las tablas Sales.SalesOrderHeader_inmem y Sales.SalesOrderDetail_inmem, y también usa búsquedas de puntos en las columnas de clave principal en las tablas Production.Product_inmem y Sales.SpecialOffer_inmem.</span><span class="sxs-lookup"><span data-stu-id="e2a87-224">The workload relies on inserts and point lookups in the tables Sales.SalesOrderHeader_inmem and Sales.SalesOrderDetail_inmem, and it also relies on point lookups on the primary key columns in the tables Production.Product_inmem and Sales.SpecialOffer_inmem.</span></span>  
  
 <span data-ttu-id="e2a87-225">Sales.SalesOrderHeader_inmem tiene tres índices, que son todos índices HASH por motivos de rendimiento, y porque no se necesita ningún examen ordenado o recorrido de intervalo para la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-225">Sales.SalesOrderHeader_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="e2a87-226">Índice HASH de (SalesOrderID): bucket_count tiene un tamaño de 10 millones (redondeado hasta 16 millones), ya que el número esperado de pedidos de venta es 10 millones</span><span class="sxs-lookup"><span data-stu-id="e2a87-226">HASH index on (SalesOrderID): bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="e2a87-227">Índice HASH de (SalesPersonID): el bucket_count es 1 millón.</span><span class="sxs-lookup"><span data-stu-id="e2a87-227">HASH index on (SalesPersonID): bucket_count is 1 million.</span></span> <span data-ttu-id="e2a87-228">El conjunto de datos especificado no tiene muchos vendedores, pero permite el crecimiento futuro, y además no hay penalización de rendimiento por las búsquedas de puntos si el valor bucket_count está sobredimensionado.</span><span class="sxs-lookup"><span data-stu-id="e2a87-228">The data set provided does not have a lot of sales persons, but this allows for future growth, plus you don't pay a performance penalty for point lookups if the bucket_count is oversized.</span></span>  
  
-   <span data-ttu-id="e2a87-229">Índice HASH de (CustomerID): el bucket_count es 1 millón.</span><span class="sxs-lookup"><span data-stu-id="e2a87-229">HASH index on (CustomerID): bucket_count is 1 million.</span></span> <span data-ttu-id="e2a87-230">El conjunto de datos especificado no tiene muchos clientes, pero permite el crecimiento futuro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-230">The data set provided does not have a lot of customers, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="e2a87-231">Sales.SalesOrderDetail_inmem tiene tres índices, que son todos índices HASH por motivos de rendimiento, y porque no se necesita ningún examen ordenado o recorrido de intervalo para la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-231">Sales.SalesOrderDetail_inmem has three indexes, which are all HASH indexes for performance reasons, and because no ordered or range scans are needed for the workload.</span></span>  
  
-   <span data-ttu-id="e2a87-232">Índice HASH de (SalesOrderID, SalesOrderDetailID): este es el índice de clave principal, y aunque las búsquedas en (SalesOrderID, SalesOrderDetailID) serán poco frecuentes, el uso de un índice hash para la clave acelera las inserciones de filas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-232">HASH index on (SalesOrderID, SalesOrderDetailID): this is the primary key index, and even though lookups on (SalesOrderID, SalesOrderDetailID) will be infrequent, using a hash index for the key speeds up row inserts.</span></span> <span data-ttu-id="e2a87-233">El bucket_count tiene un tamaño de 50 millones (redondeado hasta 67 millones): el número esperado de pedidos de venta es de 10 millones y tiene un tamaño promedio de 5 artículos por pedido.</span><span class="sxs-lookup"><span data-stu-id="e2a87-233">The bucket_count is sized at 50 million (rounded up to 67 million): the expected number of sales orders is 10 million, and this is sized to have an average of 5 items per order</span></span>  
  
-   <span data-ttu-id="e2a87-234">Índice HASH de (SalesOrderID): las búsquedas por pedido de venta son frecuentes; es conveniente buscar todos los artículos correspondientes a un único pedido.</span><span class="sxs-lookup"><span data-stu-id="e2a87-234">HASH index on (SalesOrderID): lookups by sales order are frequent: you will want to find all the line items corresponding to a single order.</span></span>  <span data-ttu-id="e2a87-235">bucket_count tiene un tamaño de 10 millones (redondeado hasta 16 millones), ya que el número esperado de pedidos de venta es 10 millones</span><span class="sxs-lookup"><span data-stu-id="e2a87-235">bucket_count is sized at 10 million (rounded up to 16 million), because the expected number of sales orders is 10 million</span></span>  
  
-   <span data-ttu-id="e2a87-236">Índice HASH de (ProductID): el bucket_count es 1 millón.</span><span class="sxs-lookup"><span data-stu-id="e2a87-236">HASH index on (ProductID): bucket_count is 1 million.</span></span> <span data-ttu-id="e2a87-237">El conjunto de datos especificado no tiene muchos productos, pero permite el crecimiento futuro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-237">The data set provided does not have a lot of product, but this allows for future growth.</span></span>  
  
 <span data-ttu-id="e2a87-238">Production.Product_inmem tiene tres índices</span><span class="sxs-lookup"><span data-stu-id="e2a87-238">Production.Product_inmem has three indexes</span></span>  
  
-   <span data-ttu-id="e2a87-239">Índice HASH de (ProductID): las búsquedas de ProductID son la ruta crítica para la carga de trabajo de demostración, por lo que es un índice hash</span><span class="sxs-lookup"><span data-stu-id="e2a87-239">HASH index on (ProductID): lookups on ProductID are in the critical path for the demo workload, therefore this is a hash index</span></span>  
  
-   <span data-ttu-id="e2a87-240">Índice no clúster de (Name): permitirá exámenes ordenados de los nombres de producto</span><span class="sxs-lookup"><span data-stu-id="e2a87-240">NONCLUSTERED index on (Name): this will allow ordered scans of product names</span></span>  
  
-   <span data-ttu-id="e2a87-241">Índice no clúster de (ProductNumber): permitirá exámenes ordenados de los números de producto</span><span class="sxs-lookup"><span data-stu-id="e2a87-241">NONCLUSTERED index on (ProductNumber): this will allow ordered scans of product numbers</span></span>  
  
 <span data-ttu-id="e2a87-242">Sales.SpecialOffer_inmem tiene un índice HASH en (SpecialOfferID): las búsquedas de puntos de ofertas especiales son una parte crítica de la carga de trabajo de demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-242">Sales.SpecialOffer_inmem has one HASH index on (SpecialOfferID): point lookups of special offers are in the critical part of the demo workload.</span></span> <span data-ttu-id="e2a87-243">El bucket_count tiene un tamaño de 1 millón para permitir el crecimiento futuro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-243">The bucket_count is sized at 1 million to allow for future growth.</span></span>  
  
 <span data-ttu-id="e2a87-244">No se hace referencia a Sales.SpecialOfferProduct_inmem en la carga de trabajo de demostración, por lo que no hay necesidad de usar índices hash en esta tabla para optimizar la carga de trabajo; los índices de (SpecialOfferID, ProductID) y (ProductID) no son agrupados.</span><span class="sxs-lookup"><span data-stu-id="e2a87-244">Sales.SpecialOfferProduct_inmem is not referenced in the demo workload, and thus there is no apparent need to use hash indexes on this table to optimize the workload - the indexes on (SpecialOfferID, ProductID) and (ProductID) are NONCLUSTERED.</span></span>  
  
 <span data-ttu-id="e2a87-245">Observe que en la información anterior algunos valores de bucket_count están sobredimensionados, pero no los bucket_counts de los índices de SalesOrderHeader_inmem y SalesOrderDetail_inmem: tienen un tamaño para 10 millones de pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-245">Notice that in the above some of the bucket_counts are over-sized, but not the bucket_counts for the indexes on SalesOrderHeader_inmem and SalesOrderDetail_inmem: they are sized for just 10 million sales orders.</span></span> <span data-ttu-id="e2a87-246">Esto se hace para permitir la instalación del ejemplo en sistemas con poca disponibilidad de memoria, aunque en esos casos la carga de trabajo de demostración producirá un error si no hay memoria suficiente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-246">This was done to allow installing the sample on systems with low memory availability, although in those cases the demo workload will fail with out-of-memory.</span></span> <span data-ttu-id="e2a87-247">Si desea escalar el ejemplo más allá de 10 millones de pedidos de venta, no dude en aumentar los números de cubos en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="e2a87-247">If you do want to scale well beyond 10 million sales orders, feel free to increase the bucket counts accordingly.</span></span>  
  
#### <a name="considerations-for-memory-utilization"></a><span data-ttu-id="e2a87-248">Consideraciones sobre el uso de memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-248">Considerations for memory utilization</span></span>  
 <span data-ttu-id="e2a87-249">El uso de memoria en la base de datos de ejemplo, tanto antes como después de ejecutar la carga de trabajo de demostración, se describe en la sección [Uso de memoria para las tablas optimizadas para memoria](#Memoryutilizationforthememory-optimizedtables).</span><span class="sxs-lookup"><span data-stu-id="e2a87-249">Memory utilization in the sample database, both before and after running the demo workload, is discussed in the Section [Memory utilization for the memory-optimized tables](#Memoryutilizationforthememory-optimizedtables).</span></span>  
  
### <a name="stored-procedures-added-by-the-sample"></a><span data-ttu-id="e2a87-250">Procedimientos almacenados agregados por el ejemplo</span><span class="sxs-lookup"><span data-stu-id="e2a87-250">Stored Procedures added by the sample</span></span>  
 <span data-ttu-id="e2a87-251">Los dos procedimientos almacenados principales para insertar pedidos de venta y actualizar los detalles de envío son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="e2a87-251">The two key stored procedures for inserting sales order and updating shipping details are as follows:</span></span>  
  
-   <span data-ttu-id="e2a87-252">Sales.usp_InsertSalesOrder_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-252">Sales.usp_InsertSalesOrder_inmem</span></span>  
  
    -   <span data-ttu-id="e2a87-253">Inserta un nuevo pedido de venta en la base de datos y genera el SalesOrderID para ese pedido.</span><span class="sxs-lookup"><span data-stu-id="e2a87-253">Inserts a new sales order in the database and outputs the SalesOrderID for that sales order.</span></span> <span data-ttu-id="e2a87-254">Como parámetros de entrada toma los detalles del encabezado del pedido de venta, así como los artículos del pedido.</span><span class="sxs-lookup"><span data-stu-id="e2a87-254">As input parameters it takes details for the sales order header, as well as the line items in the order.</span></span>  
  
    -   <span data-ttu-id="e2a87-255">Parámetro de salida:</span><span class="sxs-lookup"><span data-stu-id="e2a87-255">Output parameter:</span></span>  
  
        -   <span data-ttu-id="e2a87-256">@SalesOrderID int: el valor SalesOrderID del pedido de venta que se acaba de insertar</span><span class="sxs-lookup"><span data-stu-id="e2a87-256">@SalesOrderID int - the SalesOrderID for the sales order that was just inserted</span></span>  
  
    -   <span data-ttu-id="e2a87-257">Parámetros de entrada (obligatorios):</span><span class="sxs-lookup"><span data-stu-id="e2a87-257">Input parameters (required):</span></span>  
  
        -   <span data-ttu-id="e2a87-258">@DueDate datetime2</span><span class="sxs-lookup"><span data-stu-id="e2a87-258">@DueDate datetime2</span></span>  
  
        -   <span data-ttu-id="e2a87-259">@CustomerID int</span><span class="sxs-lookup"><span data-stu-id="e2a87-259">@CustomerID int</span></span>  
  
        -   <span data-ttu-id="e2a87-260">@BillToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-260">@BillToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-261">@ShipToAddressID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-261">@ShipToAddressID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-262">@ShipMethodID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-262">@ShipMethodID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-263">@SalesOrderDetails Sales.SalesOrderDetailType_inmem: TVP que contiene los elementos de línea del pedido</span><span class="sxs-lookup"><span data-stu-id="e2a87-263">@SalesOrderDetails Sales.SalesOrderDetailType_inmem - TVP that contains the line items of the order</span></span>  
  
    -   <span data-ttu-id="e2a87-264">Parámetros de entrada (opcionales):</span><span class="sxs-lookup"><span data-stu-id="e2a87-264">Input parameters (optional):</span></span>  
  
        -   <span data-ttu-id="e2a87-265">@Status [tinyint]</span><span class="sxs-lookup"><span data-stu-id="e2a87-265">@Status [tinyint]</span></span>  
  
        -   <span data-ttu-id="e2a87-266">@OnlineOrderFlag [bit]</span><span class="sxs-lookup"><span data-stu-id="e2a87-266">@OnlineOrderFlag [bit]</span></span>  
  
        -   <span data-ttu-id="e2a87-267">@PurchaseOrderNumber [nvarchar](25\)</span><span class="sxs-lookup"><span data-stu-id="e2a87-267">@PurchaseOrderNumber [nvarchar](25\)</span></span>  
  
        -   <span data-ttu-id="e2a87-268">@AccountNumber [nvarchar](15\)</span><span class="sxs-lookup"><span data-stu-id="e2a87-268">@AccountNumber [nvarchar](15\)</span></span>  
  
        -   <span data-ttu-id="e2a87-269">@SalesPersonID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-269">@SalesPersonID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-270">@TerritoryID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-270">@TerritoryID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-271">@CreditCardID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-271">@CreditCardID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-272">@CreditCardApprovalCode [varchar](15\)</span><span class="sxs-lookup"><span data-stu-id="e2a87-272">@CreditCardApprovalCode [varchar](15\)</span></span>  
  
        -   <span data-ttu-id="e2a87-273">@CurrencyRateID [int]</span><span class="sxs-lookup"><span data-stu-id="e2a87-273">@CurrencyRateID [int]</span></span>  
  
        -   <span data-ttu-id="e2a87-274">@Comment nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="e2a87-274">@Comment nvarchar(128)</span></span>  
  
-   <span data-ttu-id="e2a87-275">Sales.usp_UpdateSalesOrderShipInfo_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-275">Sales.usp_UpdateSalesOrderShipInfo_inmem</span></span>  
  
    -   <span data-ttu-id="e2a87-276">Actualice la información de envío para un pedido de venta determinado.</span><span class="sxs-lookup"><span data-stu-id="e2a87-276">Update the shipping information for a given sales order.</span></span> <span data-ttu-id="e2a87-277">Esto también actualizará la información de envío de todos los artículos del pedido de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-277">This will also update the shipping information for all line items of the sales order.</span></span>  
  
    -   <span data-ttu-id="e2a87-278">Se trata de un procedimiento contenedor para los procedimientos almacenados compilados de forma nativa Sales.usp_UpdateSalesOrderShipInfo_native con lógica de reintento para abordar posibles conflictos (inesperados) con las transacciones simultáneas que actualizan el mismo pedido.</span><span class="sxs-lookup"><span data-stu-id="e2a87-278">This is a wrapper procedure for the natively compiled stored procedures Sales.usp_UpdateSalesOrderShipInfo_native with retry logic to deal with (unexpected) potential conflicts with concurrent transactions updating the same order.</span></span> <span data-ttu-id="e2a87-279">Para obtener más información acerca de la lógica de reintento, vea [este tema](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx)en los Libros en pantalla.</span><span class="sxs-lookup"><span data-stu-id="e2a87-279">For more information about retry logic see the Books Online topic [here](https://technet.microsoft.com/library/dn169141\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="e2a87-280">Sales.usp_UpdateSalesOrderShipInfo_native</span><span class="sxs-lookup"><span data-stu-id="e2a87-280">Sales.usp_UpdateSalesOrderShipInfo_native</span></span>  
  
    -   <span data-ttu-id="e2a87-281">Este es el procedimiento almacenado compilado de forma nativa que procesa realmente la actualización de la información de envío.</span><span class="sxs-lookup"><span data-stu-id="e2a87-281">This is the natively compiled stored procedure that actually processes the update to the shipping information.</span></span> <span data-ttu-id="e2a87-282">Está pensado para que se le llame desde el procedimiento almacenado contenedor Sales.usp_UpdateSalesOrderShipInfo_inmem.</span><span class="sxs-lookup"><span data-stu-id="e2a87-282">It is means to be called from the wrapper stored procedure Sales.usp_UpdateSalesOrderShipInfo_inmem.</span></span> <span data-ttu-id="e2a87-283">Si el cliente puede resolver los errores e implementa lógica de reintento, puede llamar a este procedimiento directamente, en lugar de usar el procedimiento almacenado contenedor.</span><span class="sxs-lookup"><span data-stu-id="e2a87-283">If the client can deal with failures and implements retry logic, you can call this procedure directly, rather than using the wrapper stored procedure.</span></span>  
  
 <span data-ttu-id="e2a87-284">El procedimiento almacenado siguiente se emplea para la carga de trabajo de demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-284">The following stored procedure is used for the demo workload.</span></span>  
  
-   <span data-ttu-id="e2a87-285">Demo.usp_DemoReset</span><span class="sxs-lookup"><span data-stu-id="e2a87-285">Demo.usp_DemoReset</span></span>  
  
    -   <span data-ttu-id="e2a87-286">Restablece la demostración vaciando y reinicializando las tablas SalesOrderHeader y SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="e2a87-286">Resets the demo by emptying and reseeding the SalesOrderHeader and SalesOrderDetail tables.</span></span>  
  
 <span data-ttu-id="e2a87-287">Los procedimientos almacenados siguientes se usan para insertar y eliminar información de las tablas optimizadas para memoria garantizando la integridad del dominio y referencial.</span><span class="sxs-lookup"><span data-stu-id="e2a87-287">The following stored procedures are used for inserting in and deleting from memory-optimized tables while guaranteeing domain and referential integrity.</span></span>  
  
-   <span data-ttu-id="e2a87-288">Production.usp_InsertProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-288">Production.usp_InsertProduct_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-289">Production.usp_DeleteProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-289">Production.usp_DeleteProduct_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-290">Sales.usp_InsertSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-290">Sales.usp_InsertSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-291">Sales.usp_DeleteSpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-291">Sales.usp_DeleteSpecialOffer_inmem</span></span>  
  
-   <span data-ttu-id="e2a87-292">Sales.usp_InsertSpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-292">Sales.usp_InsertSpecialOfferProduct_inmem</span></span>  
  
 <span data-ttu-id="e2a87-293">Por último, el procedimiento almacenado siguiente se usa para comprobar la integridad del dominio y referencial.</span><span class="sxs-lookup"><span data-stu-id="e2a87-293">Finally the following stored procedure is used to verify domain and referential integrity.</span></span>  
  
1.  <span data-ttu-id="e2a87-294">dbo.usp_ValidateIntegrity</span><span class="sxs-lookup"><span data-stu-id="e2a87-294">dbo.usp_ValidateIntegrity</span></span>  
  
    -   <span data-ttu-id="e2a87-295">Parámetro opcional: @object_id, identificador del objeto cuya integridad se va a validar</span><span class="sxs-lookup"><span data-stu-id="e2a87-295">Optional parameter: @object_id - ID of the object to validate integrity for</span></span>  
  
    -   <span data-ttu-id="e2a87-296">Este procedimiento usa las tablas dbo.DomainIntegrity, dbo.ReferentialIntegrity y dbo.UniqueIntegrity para las reglas de integridad que es necesario comprobar; el ejemplo rellena estas tablas según las restricciones CHECK, UNIQUE y de clave externa existentes en las tablas originales de la base de datos AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e2a87-296">This procedure relies on the tables dbo.DomainIntegrity, dbo.ReferentialIntegrity, and dbo.UniqueIntegrity for the integrity rules that need to be verified - the sample populates these tables based on the check, foreign key, and unique constraints that exist for the original tables in the AdventureWorks database.</span></span>  
  
    -   <span data-ttu-id="e2a87-297">Usa los procedimientos del asistente dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck y dbo.GenerateUQCheck para generar el código T-SQL necesario para realizar las comprobaciones de integridad.</span><span class="sxs-lookup"><span data-stu-id="e2a87-297">It relies on the helper procedures dbo.usp_GenerateCKCheck, dbo.usp_GenerateFKCheck, and dbo.GenerateUQCheck to generate the T-SQL needed for performing the integrity checks.</span></span>  
  
##  <a name="PerformanceMeasurementsusingtheDemoWorkload"></a> <span data-ttu-id="e2a87-298">Medidas de rendimiento con la carga de trabajo de demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-298">Performance Measurements using the Demo Workload</span></span>  
 <span data-ttu-id="e2a87-299">Ostress es una herramienta de línea de comandos desarrollada por el equipo de soporte técnico de Microsoft CSS SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e2a87-299">Ostress is a command-line tool that was developed by the Microsoft CSS SQL Server support team.</span></span> <span data-ttu-id="e2a87-300">Esta herramienta se puede usar para ejecutar consultas o ejecutar procedimientos almacenados en paralelo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-300">This tool can be used to execute queries or run stored procedures in parallel.</span></span> <span data-ttu-id="e2a87-301">Puede configurar el número de subprocesos para ejecutar una instrucción T-SQL proporcionada en paralelo y puede especificar cuántas veces se debe ejecutar la instrucción en este subproceso; ostress recorrerá los subprocesos y ejecutará la instrucción en todos ellos en paralelo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-301">You can configure the number of threads to run a given T-SQL statement in parallel, and you can specify how many times the statement should be executed on this thread; ostress will spin up the threads and execute the statement on all threads in parallel.</span></span> <span data-ttu-id="e2a87-302">Una vez que concluya la ejecución en todos los subprocesos, ostress notificará el tiempo empleado en finalizar la ejecución en todos los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-302">After execution finishes for all threads, ostress will report the time taken for all threads to finish execution.</span></span>  
  
### <a name="installing-ostress"></a><span data-ttu-id="e2a87-303">Instalar ostress</span><span class="sxs-lookup"><span data-stu-id="e2a87-303">Installing ostress</span></span>  
 <span data-ttu-id="e2a87-304">Ostress se instala como parte de las utilidades de RML; no hay ninguna instalación independiente para ostress.</span><span class="sxs-lookup"><span data-stu-id="e2a87-304">Ostress is installed as part of the RML Utilities; there is no standalone installation for ostress.</span></span>  
  
 <span data-ttu-id="e2a87-305">Pasos para la instalación:</span><span class="sxs-lookup"><span data-stu-id="e2a87-305">Installation steps:</span></span>  
  
1.  <span data-ttu-id="e2a87-306">Descargue y ejecute el paquete de instalación x64 para las utilidades de RML desde la página siguiente: [Download Report Markup Language (RML) for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=4511) (Descarga de Report Markup Language (RML) para SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e2a87-306">Download and run the x64 installation package for the RML utilities from the following page: [Download Report Markup Language (RML) for SQL Server](https://www.microsoft.com/en-us/download/details.aspx?id=4511)</span></span>

2.  <span data-ttu-id="e2a87-307">Si aparece un cuadro de diálogo que indica que algunos archivos están en uso, haga clic en "Continue" (Continuar).</span><span class="sxs-lookup"><span data-stu-id="e2a87-307">If there is a dialog box saying certain files are in use, click 'Continue'</span></span>  
  
### <a name="running-ostress"></a><span data-ttu-id="e2a87-308">Ejecutar ostress</span><span class="sxs-lookup"><span data-stu-id="e2a87-308">Running ostress</span></span>  
 <span data-ttu-id="e2a87-309">Ostress se ejecuta desde el símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-309">Ostress is run from the command-line prompt.</span></span> <span data-ttu-id="e2a87-310">Es mejor ejecutar la herramienta desde "RML Cmd Prompt”, que se instala como parte de las utilidades de RML.</span><span class="sxs-lookup"><span data-stu-id="e2a87-310">It is most convenient to run the tool from the "RML Cmd Prompt", which is installed as part of the RML Utilities.</span></span>  
  
 <span data-ttu-id="e2a87-311">Para abrir RML Cmd Prompt, siga estas instrucciones:</span><span class="sxs-lookup"><span data-stu-id="e2a87-311">To open the RML Cmd Prompt follow these instructions:</span></span>  
  
 <span data-ttu-id="e2a87-312">En Windows Server 2012 [R2] y en Windows 8 y 8.1, haga clic en la tecla Windows para abrir el menú Inicio y escriba "rml".</span><span class="sxs-lookup"><span data-stu-id="e2a87-312">In Windows Server 2012 [R2] and in Windows 8 and 8.1, open the start menu by clicking the Windows key, and type 'rml'.</span></span> <span data-ttu-id="e2a87-313">Haga clic en "RML Cmd Prompt", que aparecerá en la lista de resultados de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="e2a87-313">Click on "RML Cmd Prompt", which will be in the list of search results.</span></span>  
  
 <span data-ttu-id="e2a87-314">Asegúrese de que el símbolo del sistema se encuentra en la carpeta de instalación de las utilidades de RML.</span><span class="sxs-lookup"><span data-stu-id="e2a87-314">Ensure that the command prompt is located in the RML Utilities installation folder.</span></span>  
  
 <span data-ttu-id="e2a87-315">Las opciones de línea de comandos para ostress se pueden ver si se ejecuta ostress.exe sin ninguna opción de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-315">The command-line options for ostress can be seen when simply running ostress.exe without any command-line options.</span></span> <span data-ttu-id="e2a87-316">Las opciones principales que hay que tener en cuenta para ejecutar ostress con este ejemplo son:</span><span class="sxs-lookup"><span data-stu-id="e2a87-316">The main options to consider for running ostress with this sample are:</span></span>  
  
-   <span data-ttu-id="e2a87-317">-S nombre de la instancia de Microsoft SQL Server a la que conectarse</span><span class="sxs-lookup"><span data-stu-id="e2a87-317">-S name of Microsoft SQL Server instance to connect to</span></span>  
  
-   <span data-ttu-id="e2a87-318">-E usar autenticación de Windows para conectarse (valor predeterminado). Si se usa la autenticación de SQL Server, utilice las opciones -U y -P para especificar el nombre de usuario y la contraseña, respectivamente</span><span class="sxs-lookup"><span data-stu-id="e2a87-318">-E use Windows authentication to connect (default); if you use SQL Server authentication, use the options -U and -P to specify the username and password, respectively</span></span>  
  
-   <span data-ttu-id="e2a87-319">-d nombre de la base de datos; para este ejemplo, AdventureWorks2014</span><span class="sxs-lookup"><span data-stu-id="e2a87-319">-d name of the database, for this example AdventureWorks2014</span></span>  
  
-   <span data-ttu-id="e2a87-320">-Q instrucción T-SQL que se va a ejecutar</span><span class="sxs-lookup"><span data-stu-id="e2a87-320">-Q the T-SQL statement to be executed</span></span>  
  
-   <span data-ttu-id="e2a87-321">-n número de conexiones que procesan cada archivo de entrada o consulta</span><span class="sxs-lookup"><span data-stu-id="e2a87-321">-n number of connections processing each input file/query</span></span>  
  
-   <span data-ttu-id="e2a87-322">-r número de iteraciones para que cada conexión ejecute cada archivo de entrada o consulta</span><span class="sxs-lookup"><span data-stu-id="e2a87-322">-r the number of iterations for each connection to execute each input file/query</span></span>  
  
### <a name="demo-workload"></a><span data-ttu-id="e2a87-323">Carga de trabajo de demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-323">Demo Workload</span></span>  
 <span data-ttu-id="e2a87-324">El procedimiento almacenado principal que se usa en la carga de trabajo de demostración es Sales.usp_InsertSalesOrder_inmem/ondisk.</span><span class="sxs-lookup"><span data-stu-id="e2a87-324">The main stored procedure used in the demo workload is Sales.usp_InsertSalesOrder_inmem/ondisk.</span></span> <span data-ttu-id="e2a87-325">El script siguiente crea un parámetro con valores de tabla (TVP) con datos de ejemplo y llama al procedimiento para insertar un pedido de venta con 5 artículos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-325">The script in the below constructs a table-valued parameter (TVP) with sample data, and calls the procedure to insert a sales order with 5 line items.</span></span>  
  
 <span data-ttu-id="e2a87-326">La herramienta ostress se emplea para ejecutar las llamadas a procedimientos almacenados en paralelo, con el fin de simular que los clientes insertan los pedidos de venta simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-326">The ostress tool is used to execute the stored procedure calls in parallel, to simulate clients inserting sales orders concurrently.</span></span>  
  
 <span data-ttu-id="e2a87-327">Restablezca la demostración después de cada prueba de esfuerzo ejecutando Demo.usp_DemoReset.</span><span class="sxs-lookup"><span data-stu-id="e2a87-327">Reset the demo after each stress run executing Demo.usp_DemoReset.</span></span> <span data-ttu-id="e2a87-328">Este procedimiento elimina las filas de las tablas optimizadas para memoria, trunca las tablas basadas en disco y ejecuta un punto de comprobación de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-328">This procedure deletes the rows in the memory-optimized tables, truncates the disk-based tables, and executes a database checkpoint.</span></span>  
  
 <span data-ttu-id="e2a87-329">El script siguiente se ejecuta simultáneamente para simular una carga de trabajo de procesamiento de pedidos de venta:</span><span class="sxs-lookup"><span data-stu-id="e2a87-329">The following script is executed concurrently to simulate a sales order processing workload:</span></span>  
  
```  
DECLARE   
      @i int = 0,   
      @od Sales.SalesOrderDetailType_inmem,   
      @SalesOrderID int,   
      @DueDate datetime2 = sysdatetime(),   
      @CustomerID int = rand() * 8000,   
      @BillToAddressID int = rand() * 10000,   
      @ShipToAddressID int = rand() * 10000,   
      @ShipMethodID int = (rand() * 5) + 1;   
  
INSERT INTO @od   
SELECT OrderQty, ProductID, SpecialOfferID   
FROM Demo.DemoSalesOrderDetailSeed   
WHERE OrderID= cast((rand()*106) + 1 as int);   
  
WHILE (@i < 20)   
BEGIN;   
      EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od;   
      SET @i += 1   
END  
  
```  
  
 <span data-ttu-id="e2a87-330">Con este script, cada pedido de ejemplo que se crea se inserta 20 veces, mediante 20 procedimientos almacenados que se ejecutan en un bucle WHILE.</span><span class="sxs-lookup"><span data-stu-id="e2a87-330">With this script, each sample order that is constructed is inserted 20 times, through 20 stored procedures executed in a WHILE loop.</span></span> <span data-ttu-id="e2a87-331">El bucle se usa para tener en cuenta el hecho de que la base de datos se emplea para crear el pedido de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-331">The loop is used to account for the fact that the database is used to construct the sample order.</span></span> <span data-ttu-id="e2a87-332">En los entornos de producción típicos, la aplicación de nivel intermedio creará el pedido de venta que se va a insertar.</span><span class="sxs-lookup"><span data-stu-id="e2a87-332">In typical production environments, the mid-tier application will construct the sales order to be inserted.</span></span>  
  
 <span data-ttu-id="e2a87-333">El script anterior inserta los pedidos de venta en tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-333">The above script inserts sales orders into memory-optimized tables.</span></span> <span data-ttu-id="e2a87-334">El script para insertar pedidos de venta en tablas basadas en disco se deriva reemplazando las dos instancias de "_inmem" por "_ondisk".</span><span class="sxs-lookup"><span data-stu-id="e2a87-334">The script to insert sales orders into disk-based tables is derived by replacing the two occurrences of '_inmem' with '_ondisk'.</span></span>  
  
 <span data-ttu-id="e2a87-335">Se usará la herramienta ostress para ejecutar los scripts con varias conexiones simultáneas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-335">We will use the ostress tool to execute the scripts using several concurrent connections.</span></span> <span data-ttu-id="e2a87-336">Se usará el parámetro "-n" para controlar el número de conexiones y el parámetro "r" para controlar cuántas veces se ejecuta el script en cada conexión.</span><span class="sxs-lookup"><span data-stu-id="e2a87-336">We will use the parameter '-n' to control the number of connections, and the parameter 'r' to control how many times the script is executed on each connection.</span></span>  
  
#### <a name="running-the-workload"></a><span data-ttu-id="e2a87-337">Ejecutar la carga de trabajo</span><span class="sxs-lookup"><span data-stu-id="e2a87-337">Running the Workload</span></span>  
 <span data-ttu-id="e2a87-338">Para probar la escala insertamos 10 millones de pedidos de venta usando 100 conexiones.</span><span class="sxs-lookup"><span data-stu-id="e2a87-338">To test at scale we insert 10 million sales orders, using 100 connections.</span></span> <span data-ttu-id="e2a87-339">Esta prueba funciona razonablemente bien en un servidor modesto (por ejemplo, 8 núcleos físicos y 16 lógicos) y con un almacenamiento SSD básico para el registro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-339">This test performs reasonably on a modest server (e.g., 8 physical, 16 logical cores), and basic SSD storage for the log.</span></span> <span data-ttu-id="e2a87-340">Si la prueba no funciona correctamente en el hardware, vea la sección [Solucionar problemas de pruebas de ejecución lenta](#Troubleshootingslow-runningtests). Si quiere reducir el nivel de esfuerzo de esta prueba, disminuya el número de conexiones cambiando el parámetro "-n".</span><span class="sxs-lookup"><span data-stu-id="e2a87-340">If the test does not perform well on your hardware, take look at the Section [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).If you want to reduce the level of stress for this test, lower the number of connections by changing the parameter '-n'.</span></span> <span data-ttu-id="e2a87-341">Por ejemplo, para reducir el número de conexiones a 40, cambie el parámetro "-n100" a "-n40".</span><span class="sxs-lookup"><span data-stu-id="e2a87-341">For example to lower the connection count to 40, change the parameter '-n100' to '-n40'.</span></span>  
  
 <span data-ttu-id="e2a87-342">Como medida de rendimiento de la carga de trabajo usamos el tiempo transcurrido notificado por ostress.exe después de ejecutar la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-342">As a performance measure for the workload we use the elapsed time as reported by ostress.exe after running the workload.</span></span>  
  
 <span data-ttu-id="e2a87-343">En las medidas e instrucciones siguientes se usa una carga de trabajo que inserta 10 millones de pedidos de ventas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-343">The below instructions and measurements use a workload that inserts 10 million sales orders.</span></span> <span data-ttu-id="e2a87-344">Para obtener instrucciones para ejecutar una carga de trabajo reducida que inserta 1 millón de pedidos de ventas, vea las instrucciones del archivo “In-Memory OLTP\readme.txt” incluido en el archivo SQLServer2016CTP3Samples.zip.</span><span class="sxs-lookup"><span data-stu-id="e2a87-344">For instructions to run a scaled-down workload inserting 1 million sales orders, see the instructions in 'In-Memory OLTP\readme.txt' that is part of the SQLServer2016CTP3Samples.zip archive.</span></span>  
  
##### <a name="memory-optimized-tables"></a><span data-ttu-id="e2a87-345">Tablas con optimización para memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-345">Memory-optimized tables</span></span>  
 <span data-ttu-id="e2a87-346">Empezaremos ejecutando la carga de trabajo en las tablas optimizadas para memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-346">We will start by running the workload on memory-optimized tables.</span></span> <span data-ttu-id="e2a87-347">El comando siguiente abre 100 subprocesos, cada uno de los cuales se ejecuta para 5.000 iteraciones.</span><span class="sxs-lookup"><span data-stu-id="e2a87-347">The following command opens 100 threads, each running for 5,000 iterations.</span></span>  <span data-ttu-id="e2a87-348">Cada iteración inserta 20 pedidos de venta en transacciones diferentes.</span><span class="sxs-lookup"><span data-stu-id="e2a87-348">Each iteration inserts 20 sales orders in separate transactions.</span></span> <span data-ttu-id="e2a87-349">Hay 20 inserciones por iteración para compensar el hecho de que la base de datos se usa para generar los datos que se van a insertar.</span><span class="sxs-lookup"><span data-stu-id="e2a87-349">There are 20 inserts per iteration to compensate for the fact that the database is used to generate the data to be inserted.</span></span> <span data-ttu-id="e2a87-350">Esto produce un total de 20 \* 5 000 \* 100 = 10 000 000 inserciones de pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-350">This yield a total of 20 \* 5,000 \* 100 = 10,000,000 sales order inserts.</span></span>  
  
 <span data-ttu-id="e2a87-351">Abra RML Cmd Prompt y ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-351">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="e2a87-352">Haga clic en el botón Copy para copiar el comando y péguelo en el símbolo del sistema de las utilidades de RML.</span><span class="sxs-lookup"><span data-stu-id="e2a87-352">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2016CTP3 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_inmem, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_inmem @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="e2a87-353">En un servidor de prueba con un número total de 8 núcleos físicos (16 lógicos), se tardaron 2 minutos y 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-353">On one test server with a total number of 8 physical (16 logical) cores, this took 2 minutes and 5 seconds.</span></span> <span data-ttu-id="e2a87-354">En un segundo servidor de prueba con 24 núcleos físicos (48 lógicos), se tardó 1 minuto y 0 segundos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-354">On a second test server with 24 physical (48 logical) cores, this took 1 minute and 0 seconds.</span></span>  
  
 <span data-ttu-id="e2a87-355">Observe el uso de la CPU mientras se está ejecutando la carga de trabajo, por ejemplo con el Administrador de tareas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-355">Observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="e2a87-356">Verá que el uso de la CPU está cercano al 100 %.</span><span class="sxs-lookup"><span data-stu-id="e2a87-356">You will see that CPU utilization is close to 100%.</span></span> <span data-ttu-id="e2a87-357">De lo contrario, tiene un cuello de botella en la E/S de registro; vea también [Solucionar problemas de pruebas de ejecución lenta](#Troubleshootingslow-runningtests).</span><span class="sxs-lookup"><span data-stu-id="e2a87-357">If this is not the case, you have a log IO bottleneck see also [Troubleshooting slow-running tests](#Troubleshootingslow-runningtests).</span></span>  
  
##### <a name="disk-based-tables"></a><span data-ttu-id="e2a87-358">Tablas basadas en disco</span><span class="sxs-lookup"><span data-stu-id="e2a87-358">Disk-based tables</span></span>  
 <span data-ttu-id="e2a87-359">El comando siguiente ejecutará la carga de trabajo en tablas basadas en disco.</span><span class="sxs-lookup"><span data-stu-id="e2a87-359">The following command will run the workload on disk-based tables.</span></span> <span data-ttu-id="e2a87-360">Tenga en cuenta que esta carga de trabajo puede tardar bastante tiempo en ejecutarse, lo que se debe en gran medida a la contención de bloqueos temporales del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-360">Note that this workload may take a while to execute, which is largely due to latch contention in the system.</span></span> <span data-ttu-id="e2a87-361">Las tablas con optimización para memoria no tienen bloqueos temporales y por tanto no experimentan este problema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-361">Memory-optimized table are latch-free and thus do not suffer from this problem.</span></span>  
  
 <span data-ttu-id="e2a87-362">Abra RML Cmd Prompt y ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-362">Open the RML Cmd Prompt, and execute the following command:</span></span>  
  
 <span data-ttu-id="e2a87-363">Haga clic en el botón Copy para copiar el comando y péguelo en el símbolo del sistema de las utilidades de RML.</span><span class="sxs-lookup"><span data-stu-id="e2a87-363">Click the Copy button to copy the command, and paste it into the RML Utilities command prompt.</span></span>  
  
```  
ostress.exe -n100 -r5000 -S. -E -dAdventureWorks2016CTP3 -q -Q"DECLARE @i int = 0, @od Sales.SalesOrderDetailType_ondisk, @SalesOrderID int, @DueDate datetime2 = sysdatetime(), @CustomerID int = rand() * 8000, @BillToAddressID int = rand() * 10000, @ShipToAddressID int = rand() * 10000, @ShipMethodID int = (rand() * 5) + 1; INSERT INTO @od SELECT OrderQty, ProductID, SpecialOfferID FROM Demo.DemoSalesOrderDetailSeed WHERE OrderID= cast((rand()*106) + 1 as int); while (@i < 20) begin; EXEC Sales.usp_InsertSalesOrder_ondisk @SalesOrderID OUTPUT, @DueDate, @CustomerID, @BillToAddressID, @ShipToAddressID, @ShipMethodID, @od; set @i += 1 end"  
```  
  
 <span data-ttu-id="e2a87-364">En un servidor de prueba con un número total de 8 núcleos físicos (16 lógicos), se tardaron 41 minutos y 25 segundos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-364">On one test server with a total number of 8 physical (16 logical) cores, this took 41 minutes and 25 seconds.</span></span> <span data-ttu-id="e2a87-365">En un segundo servidor de prueba con 24 núcleos físicos (48 lógicos), se tardaron 52 minutos y 16 segundos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-365">On a second test server with 24 physical (48 logical) cores, this took 52 minutes and 16 seconds.</span></span>  
  
 <span data-ttu-id="e2a87-366">La causa principal de la diferencia de rendimiento entre las tablas optimizadas para memoria y las tablas basadas en disco en esta prueba es el hecho de que cuando se usan tablas basadas en disco, SQL Server no puede usar totalmente la CPU.</span><span class="sxs-lookup"><span data-stu-id="e2a87-366">The main factor in the performance difference between memory-optimized tables and disk-based tables in this test is the fact that when using disk-based tables, SQL Server cannot not fully utilize the CPU.</span></span> <span data-ttu-id="e2a87-367">El motivo es la contención de bloqueos temporales: las transacciones simultáneas intentan escribir en la misma página de datos; los bloqueos temporales se usan para asegurarse de que solo una transacción puede escribir en una página a la vez.</span><span class="sxs-lookup"><span data-stu-id="e2a87-367">The reason is latch contention: concurrent transactions are attempting to write to the same data page; latches are used to ensure only one transaction at a time can write to a page.</span></span> <span data-ttu-id="e2a87-368">El motor de OLTP en memoria no tiene bloqueos temporales y las filas de datos no se organizan en páginas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-368">The In-Memory OLTP engine is latch-free, and data rows are not organized in pages.</span></span> <span data-ttu-id="e2a87-369">Por tanto, las transacciones simultáneas no bloquean las inserciones de las demás, lo que permite a SQL Server usar totalmente la CPU.</span><span class="sxs-lookup"><span data-stu-id="e2a87-369">Thus, concurrent transactions do not block each other's inserts, thus enabling SQL Server to fully utilize the CPU.</span></span>  
  
 <span data-ttu-id="e2a87-370">Puede observar el uso de la CPU mientras se está ejecutando la carga de trabajo, por ejemplo con el Administrador de tareas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-370">You can observe the CPU utilization while the workload is running, for example using task manager.</span></span> <span data-ttu-id="e2a87-371">Con las tablas basadas en disco verá que el uso de la CPU está muy alejado del 100 %.</span><span class="sxs-lookup"><span data-stu-id="e2a87-371">You will see with disk-based tables the CPU utilization is far from 100%.</span></span> <span data-ttu-id="e2a87-372">En una configuración de prueba con 16 procesadores lógicos, el uso rondaría el 24 %.</span><span class="sxs-lookup"><span data-stu-id="e2a87-372">On a test configuration with 16 logical processors, the utilization would hover around 24%.</span></span>  
  
 <span data-ttu-id="e2a87-373">Opcionalmente, puede ver el número de esperas de bloqueos temporales por segundo mediante el Monitor de rendimiento, con el contador de rendimiento "\SQL Server:Bloqueos temporales\Esperas de bloqueos temporales/s".</span><span class="sxs-lookup"><span data-stu-id="e2a87-373">Optionally, you can view the number of latch waits per second using Performance Monitor, with the performance counter '\SQL Server:Latches\Latch Waits/sec'.</span></span>  
  
#### <a name="resetting-the-demo"></a><span data-ttu-id="e2a87-374">Restablecer la demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-374">Resetting the demo</span></span>  
 <span data-ttu-id="e2a87-375">Para restablecer la demostración, abra RML Cmd Prompt y ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-375">To reset the demo, open the RML Cmd Prompt, and execute the following command:</span></span>  
  
```  
ostress.exe -S. -E -dAdventureWorks2016CTP3 -Q"EXEC Demo.usp_DemoReset"  
```  
  
 <span data-ttu-id="e2a87-376">Según el hardware, puede tardar unos minutos en ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="e2a87-376">Depending on the hardware this may take a few minutes to run.</span></span>  
  
 <span data-ttu-id="e2a87-377">Se recomienda restablecer la demostración tras cada ejecución.</span><span class="sxs-lookup"><span data-stu-id="e2a87-377">We recommend a reset after every demo run.</span></span> <span data-ttu-id="e2a87-378">Como esta carga de trabajo solo realiza inserciones, cada ejecución consume más memoria, por lo que es necesario un restablecimiento para no quedarse sin memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-378">Because this workload is insert-only, each run will consume more memory, and thus a reset is required to prevent running out of memory.</span></span> <span data-ttu-id="e2a87-379">La cantidad de memoria consumida después de una ejecución se explica en la sección [Utilización de memoria después de ejecutar la carga de trabajo](#Memoryutilizationafterrunningtheworkload).</span><span class="sxs-lookup"><span data-stu-id="e2a87-379">The amount of memory consumed after a run is discussed in Section [Memory utilization after running the workload](#Memoryutilizationafterrunningtheworkload).</span></span>  
  
###  <a name="Troubleshootingslow-runningtests"></a> <span data-ttu-id="e2a87-380">Solucionar problemas de pruebas de ejecución lenta</span><span class="sxs-lookup"><span data-stu-id="e2a87-380">Troubleshooting slow-running tests</span></span>  
 <span data-ttu-id="e2a87-381">Los resultados de prueba variarán normalmente según el hardware, y también el nivel de simultaneidad empleado en la serie de pruebas.</span><span class="sxs-lookup"><span data-stu-id="e2a87-381">Test results will typically vary with hardware, and also the level of concurrency used in the test run.</span></span> <span data-ttu-id="e2a87-382">He aquí varios aspectos que hay que examinar si los resultados no son los esperados:</span><span class="sxs-lookup"><span data-stu-id="e2a87-382">A couple of things to look for if the results are not as expected:</span></span>  
  
-   <span data-ttu-id="e2a87-383">Número de transacciones simultáneas: cuando se ejecuta la carga de trabajo en un solo subproceso, el aumento del rendimiento con OLTP en memoria probablemente será menor del doble.</span><span class="sxs-lookup"><span data-stu-id="e2a87-383">Number of concurrent transactions: When running the workload on a single thread, performance gain with In-Memory OLTP will likely be less than 2X.</span></span> <span data-ttu-id="e2a87-384">La contención de bloqueos temporales solo supone un gran problema si hay un nivel elevado de simultaneidad.</span><span class="sxs-lookup"><span data-stu-id="e2a87-384">Latch contention is only a big problem if there is a high level of concurrency.</span></span>  
  
-   <span data-ttu-id="e2a87-385">Pocos núcleos disponibles para SQL Server: esto significa que habrá un bajo nivel de simultaneidad en el sistema, ya que solo puede haber tantas transacciones que se ejecutan simultáneamente como núcleos disponibles haya en SQL.</span><span class="sxs-lookup"><span data-stu-id="e2a87-385">Low number of cores available to SQL Server: This means there will be a low level of concurrency in the system, as there can only be as many concurrently executing transactions as there are cores available to SQL.</span></span>  
  
    -   <span data-ttu-id="e2a87-386">Síntoma: si la utilización de la CPU es alta cuando se ejecuta la carga de trabajo en tablas basadas en disco, significa que no hay mucha contención, lo que apunta a una falta de simultaneidad.</span><span class="sxs-lookup"><span data-stu-id="e2a87-386">Symptom: if the CPU utilization is high when running the workload on disk-based tables, this means there is not a lot of contention, pointing to a lack of concurrency.</span></span>  
  
-   <span data-ttu-id="e2a87-387">Velocidad de la unidad de registro: si la unidad de registro no puede seguir el nivel de rendimiento de transacciones del sistema, la carga de trabajo se convierte en un cuello de botella para la E/S de registro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-387">Speed of the log drive: If the log drive cannot keep up with the level of transaction throughput in the system, the workload becomes bottlenecked on log IO.</span></span> <span data-ttu-id="e2a87-388">Aunque el registro es más eficaz con OLTP en memoria, si la E/S de registro es un cuello de botella, se limita el aumento potencial de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e2a87-388">Although logging is more efficient with In-Memory OLTP, if log IO is a bottleneck, the potential performance gain is limited.</span></span>  
  
    -   <span data-ttu-id="e2a87-389">Síntoma: si la utilización de la CPU no está cercana al 100 % o tiene muchos picos cuando se ejecuta la carga de trabajo en tablas optimizadas para memoria, es posible que haya un cuello de botella de la E/S de registro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-389">Symptom: if the CPU utilization is not close to 100% or is very spiky when running the workload on memory-optimized tables, it is possible there is a log IO bottleneck.</span></span> <span data-ttu-id="e2a87-390">Esto se puede confirmar abriendo el Monitor de recursos y examinando la longitud de la cola de la unidad de registro.</span><span class="sxs-lookup"><span data-stu-id="e2a87-390">This can be confirmed by opening Resource Monitor and looking at the queue length for the log drive.</span></span>  
  
##  <a name="MemoryandDiskSpaceUtilizationintheSample"></a> <span data-ttu-id="e2a87-391">Uso de memoria y de espacio en disco del ejemplo</span><span class="sxs-lookup"><span data-stu-id="e2a87-391">Memory and Disk Space Utilization in the Sample</span></span>  
 <span data-ttu-id="e2a87-392">A continuación se describe qué cabe esperar en cuando a uso de la memoria y del espacio en disco para la base de datos de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-392">In the below we describe what to expect in terms of memory and disk space utilization for the sample database.</span></span> <span data-ttu-id="e2a87-393">También se muestran los resultados obtenidos en un servidor de prueba con 16 núcleos lógicos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-393">We also show the results we have seen in on a test server with 16 logical cores.</span></span>  
  
###  <a name="Memoryutilizationforthememory-optimizedtables"></a> <span data-ttu-id="e2a87-394">Uso de memoria para las tablas optimizadas para memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-394">Memory utilization for the memory-optimized tables</span></span>  
  
#### <a name="overall-utilization-of-the-database"></a><span data-ttu-id="e2a87-395">Utilización global de la base de datos</span><span class="sxs-lookup"><span data-stu-id="e2a87-395">Overall utilization of the database</span></span>  
 <span data-ttu-id="e2a87-396">Se puede usar la consulta siguiente para obtener la utilización de memoria total para OLTP en memoria en el sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-396">The following query can be used to obtain the total memory utilization for In-Memory OLTP in the system.</span></span>  
  
```  
SELECT type  
   , name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
 <span data-ttu-id="e2a87-397">Instantánea justo después de crearse la base de datos:</span><span class="sxs-lookup"><span data-stu-id="e2a87-397">Snapshot after the database has just been created:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-398">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="e2a87-398">**type**</span></span>|<span data-ttu-id="e2a87-399">**Nombre**</span><span class="sxs-lookup"><span data-stu-id="e2a87-399">**name**</span></span>|<span data-ttu-id="e2a87-400">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-400">**pages_MB**</span></span>|  
|<span data-ttu-id="e2a87-401">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-401">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-402">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-402">Default</span></span>|<span data-ttu-id="e2a87-403">94</span><span class="sxs-lookup"><span data-stu-id="e2a87-403">94</span></span>|  
|<span data-ttu-id="e2a87-404">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-404">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-405">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e2a87-405">DB_ID_5</span></span>|<span data-ttu-id="e2a87-406">877</span><span class="sxs-lookup"><span data-stu-id="e2a87-406">877</span></span>|  
|<span data-ttu-id="e2a87-407">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-407">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-408">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-408">Default</span></span>|<span data-ttu-id="e2a87-409">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-409">0</span></span>|  
|<span data-ttu-id="e2a87-410">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-410">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-411">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-411">Default</span></span>|<span data-ttu-id="e2a87-412">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-412">0</span></span>|  
  
 <span data-ttu-id="e2a87-413">Los distribuidores de memoria predeterminados contienen estructuras de memoria de todo el sistema y son relativamente pequeños.</span><span class="sxs-lookup"><span data-stu-id="e2a87-413">The default memory clerks contain system-wide memory structures and are relatively small.</span></span> <span data-ttu-id="e2a87-414">El distribuidor de memoria para la base de datos de usuario, en este caso la base de datos con el identificador 5, tiene unos 900 MB.</span><span class="sxs-lookup"><span data-stu-id="e2a87-414">The memory clerk for the user database, in this case database with ID 5, is about 900MB.</span></span>  
  
#### <a name="memory-utilization-per-table"></a><span data-ttu-id="e2a87-415">Utilización de memoria por tabla</span><span class="sxs-lookup"><span data-stu-id="e2a87-415">Memory utilization per table</span></span>  
 <span data-ttu-id="e2a87-416">Se puede usar la consulta siguiente para explorar en profundidad la utilización de memoria de las tablas individuales y sus índices:</span><span class="sxs-lookup"><span data-stu-id="e2a87-416">The following query can be used to drill down into the memory utilization of the individual tables and their indexes:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
 <span data-ttu-id="e2a87-417">A continuación se muestran los resultados de esta consulta para una instalación nueva del ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-417">The following shows the results of this query for a fresh installation of the sample:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-418">**Nombre de tabla**</span><span class="sxs-lookup"><span data-stu-id="e2a87-418">**Table Name**</span></span>|<span data-ttu-id="e2a87-419">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="e2a87-419">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="e2a87-420">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="e2a87-420">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="e2a87-421">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-421">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="e2a87-422">64</span><span class="sxs-lookup"><span data-stu-id="e2a87-422">64</span></span>|<span data-ttu-id="e2a87-423">3840</span><span class="sxs-lookup"><span data-stu-id="e2a87-423">3840</span></span>|  
|<span data-ttu-id="e2a87-424">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="e2a87-424">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="e2a87-425">1984</span><span class="sxs-lookup"><span data-stu-id="e2a87-425">1984</span></span>|<span data-ttu-id="e2a87-426">5504</span><span class="sxs-lookup"><span data-stu-id="e2a87-426">5504</span></span>|  
|<span data-ttu-id="e2a87-427">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-427">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="e2a87-428">15316</span><span class="sxs-lookup"><span data-stu-id="e2a87-428">15316</span></span>|<span data-ttu-id="e2a87-429">663552</span><span class="sxs-lookup"><span data-stu-id="e2a87-429">663552</span></span>|  
|<span data-ttu-id="e2a87-430">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e2a87-430">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="e2a87-431">64</span><span class="sxs-lookup"><span data-stu-id="e2a87-431">64</span></span>|<span data-ttu-id="e2a87-432">10432</span><span class="sxs-lookup"><span data-stu-id="e2a87-432">10432</span></span>|  
|<span data-ttu-id="e2a87-433">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-433">SpecialOffer_inmem</span></span>|<span data-ttu-id="e2a87-434">3</span><span class="sxs-lookup"><span data-stu-id="e2a87-434">3</span></span>|<span data-ttu-id="e2a87-435">8192</span><span class="sxs-lookup"><span data-stu-id="e2a87-435">8192</span></span>|  
|<span data-ttu-id="e2a87-436">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-436">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="e2a87-437">7168</span><span class="sxs-lookup"><span data-stu-id="e2a87-437">7168</span></span>|<span data-ttu-id="e2a87-438">147456</span><span class="sxs-lookup"><span data-stu-id="e2a87-438">147456</span></span>|  
|<span data-ttu-id="e2a87-439">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-439">Product_inmem</span></span>|<span data-ttu-id="e2a87-440">124</span><span class="sxs-lookup"><span data-stu-id="e2a87-440">124</span></span>|<span data-ttu-id="e2a87-441">12352</span><span class="sxs-lookup"><span data-stu-id="e2a87-441">12352</span></span>|  
  
 <span data-ttu-id="e2a87-442">Como puede ver, las tablas son bastante pequeñas: SalesOrderHeader_inmem tiene unos 7 MB y SalesOrderDetail_inmem unos 15 MB de tamaño.</span><span class="sxs-lookup"><span data-stu-id="e2a87-442">As you can see the tables are fairly small: SalesOrderHeader_inmem is about 7MB, and SalesOrderDetail_inmem is about 15MB in size.</span></span>  
  
 <span data-ttu-id="e2a87-443">Lo sorprendente aquí es el tamaño de la memoria asignada para los índices, en comparación con el tamaño de los datos de tabla.</span><span class="sxs-lookup"><span data-stu-id="e2a87-443">What is striking here is the size of the memory allocated for indexes, compared to the size of the table data.</span></span> <span data-ttu-id="e2a87-444">Esto se debe a que los índices hash del ejemplo tienen establecido previamente un tamaño de datos mayor.</span><span class="sxs-lookup"><span data-stu-id="e2a87-444">That is because the hash indexes in the sample are pre-sized for a larger data size.</span></span> <span data-ttu-id="e2a87-445">Observe que los índices hash tienen un tamaño fijo y por tanto su tamaño no crece junto con el tamaño de los datos de la tabla.</span><span class="sxs-lookup"><span data-stu-id="e2a87-445">Note that hash indexes have a fixed size, and thus their size will not grow with the size of data in the table.</span></span>  
  
####  <a name="Memoryutilizationafterrunningtheworkload"></a> <span data-ttu-id="e2a87-446">Utilización de memoria después de ejecutar la carga de trabajo</span><span class="sxs-lookup"><span data-stu-id="e2a87-446">Memory utilization after running the workload</span></span>  
 <span data-ttu-id="e2a87-447">Después de insertar 10 millones de pedidos de venta, la utilización total de memoria es similar a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-447">After insert 10 million sales orders, the all-up memory utilization looks similar to the following:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-448">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="e2a87-448">**type**</span></span>|<span data-ttu-id="e2a87-449">**Nombre**</span><span class="sxs-lookup"><span data-stu-id="e2a87-449">**name**</span></span>|<span data-ttu-id="e2a87-450">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-450">**pages_MB**</span></span>|  
|<span data-ttu-id="e2a87-451">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-451">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-452">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-452">Default</span></span>|<span data-ttu-id="e2a87-453">146</span><span class="sxs-lookup"><span data-stu-id="e2a87-453">146</span></span>|  
|<span data-ttu-id="e2a87-454">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-454">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-455">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e2a87-455">DB_ID_5</span></span>|<span data-ttu-id="e2a87-456">7374</span><span class="sxs-lookup"><span data-stu-id="e2a87-456">7374</span></span>|  
|<span data-ttu-id="e2a87-457">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-457">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-458">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-458">Default</span></span>|<span data-ttu-id="e2a87-459">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-459">0</span></span>|  
|<span data-ttu-id="e2a87-460">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-460">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-461">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-461">Default</span></span>|<span data-ttu-id="e2a87-462">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-462">0</span></span>|  
  
 <span data-ttu-id="e2a87-463">Como puede ver, SQL Server usa un bit por debajo de 8 GB para las tablas y los índices optimizados para memoria de la base de datos de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-463">As you can see, SQL Server is using a bit under 8GB for the memory-optimized tables and indexes in the sample database.</span></span>  
  
 <span data-ttu-id="e2a87-464">Examinando el uso detallado de memoria por tabla después de ejecutar un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-464">Looking at the detailed memory usage per table after one example run:</span></span>  
  
```  
SELECT object_name(t.object_id) AS [Table Name]  
     , memory_allocated_for_table_kb  
 , memory_allocated_for_indexes_kb  
FROM sys.dm_db_xtp_table_memory_stats dms JOIN sys.tables t   
ON dms.object_id=t.object_id  
WHERE t.type='U'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-465">**Nombre de tabla**</span><span class="sxs-lookup"><span data-stu-id="e2a87-465">**Table Name**</span></span>|<span data-ttu-id="e2a87-466">**memory_allocated_for_table_kb**</span><span class="sxs-lookup"><span data-stu-id="e2a87-466">**memory_allocated_for_table_kb**</span></span>|<span data-ttu-id="e2a87-467">**memory_allocated_for_indexes_kb**</span><span class="sxs-lookup"><span data-stu-id="e2a87-467">**memory_allocated_for_indexes_kb**</span></span>|  
|<span data-ttu-id="e2a87-468">SalesOrderDetail_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-468">SalesOrderDetail_inmem</span></span>|<span data-ttu-id="e2a87-469">5113761</span><span class="sxs-lookup"><span data-stu-id="e2a87-469">5113761</span></span>|<span data-ttu-id="e2a87-470">663552</span><span class="sxs-lookup"><span data-stu-id="e2a87-470">663552</span></span>|  
|<span data-ttu-id="e2a87-471">DemoSalesOrderDetailSeed</span><span class="sxs-lookup"><span data-stu-id="e2a87-471">DemoSalesOrderDetailSeed</span></span>|<span data-ttu-id="e2a87-472">64</span><span class="sxs-lookup"><span data-stu-id="e2a87-472">64</span></span>|<span data-ttu-id="e2a87-473">10368</span><span class="sxs-lookup"><span data-stu-id="e2a87-473">10368</span></span>|  
|<span data-ttu-id="e2a87-474">SpecialOffer_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-474">SpecialOffer_inmem</span></span>|<span data-ttu-id="e2a87-475">2</span><span class="sxs-lookup"><span data-stu-id="e2a87-475">2</span></span>|<span data-ttu-id="e2a87-476">8192</span><span class="sxs-lookup"><span data-stu-id="e2a87-476">8192</span></span>|  
|<span data-ttu-id="e2a87-477">SalesOrderHeader_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-477">SalesOrderHeader_inmem</span></span>|<span data-ttu-id="e2a87-478">1575679</span><span class="sxs-lookup"><span data-stu-id="e2a87-478">1575679</span></span>|<span data-ttu-id="e2a87-479">147456</span><span class="sxs-lookup"><span data-stu-id="e2a87-479">147456</span></span>|  
|<span data-ttu-id="e2a87-480">Product_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-480">Product_inmem</span></span>|<span data-ttu-id="e2a87-481">111</span><span class="sxs-lookup"><span data-stu-id="e2a87-481">111</span></span>|<span data-ttu-id="e2a87-482">12032</span><span class="sxs-lookup"><span data-stu-id="e2a87-482">12032</span></span>|  
|<span data-ttu-id="e2a87-483">SpecialOfferProduct_inmem</span><span class="sxs-lookup"><span data-stu-id="e2a87-483">SpecialOfferProduct_inmem</span></span>|<span data-ttu-id="e2a87-484">64</span><span class="sxs-lookup"><span data-stu-id="e2a87-484">64</span></span>|<span data-ttu-id="e2a87-485">3712</span><span class="sxs-lookup"><span data-stu-id="e2a87-485">3712</span></span>|  
|<span data-ttu-id="e2a87-486">DemoSalesOrderHeaderSeed</span><span class="sxs-lookup"><span data-stu-id="e2a87-486">DemoSalesOrderHeaderSeed</span></span>|<span data-ttu-id="e2a87-487">1984</span><span class="sxs-lookup"><span data-stu-id="e2a87-487">1984</span></span>|<span data-ttu-id="e2a87-488">5504</span><span class="sxs-lookup"><span data-stu-id="e2a87-488">5504</span></span>|  
  
 <span data-ttu-id="e2a87-489">Podemos ver un total de unos 6,5 GB de datos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-489">We can see a total of about 6.5GB of data.</span></span> <span data-ttu-id="e2a87-490">Observe que el tamaño de los índices de la tabla SalesOrderHeader_inmem y SalesOrderDetail_inmem es el mismo que el tamaño de los índices antes de insertar los pedidos de venta.</span><span class="sxs-lookup"><span data-stu-id="e2a87-490">Notice that the size of the indexes on the table SalesOrderHeader_inmem and SalesOrderDetail_inmem is the same as the size of the indexes before inserting the sales orders.</span></span> <span data-ttu-id="e2a87-491">El tamaño del índice no cambió porque ambas tablas emplean índices hash y los índices hash son estáticos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-491">The index size did not change because both tables are using hash indexes, and hash indexes are static.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="e2a87-492">Después de restablecer la demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-492">After demo reset</span></span>  
 <span data-ttu-id="e2a87-493">Se puede usar el procedimiento almacenado Demo.usp_DemoReset para restablecer la demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-493">The stored procedure Demo.usp_DemoReset can be used to reset the demo.</span></span> <span data-ttu-id="e2a87-494">Elimina los datos de las tablas SalesOrderHeader_inmem y SalesOrderDetail_inmem, y reinicializa los datos de las tablas originales SalesOrderHeader y SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="e2a87-494">It deletes the data in the tables SalesOrderHeader_inmem and SalesOrderDetail_inmem, and re-seeds the data from the original tables SalesOrderHeader and SalesOrderDetail.</span></span>  
  
 <span data-ttu-id="e2a87-495">Ahora, aunque las filas de las tablas se han eliminado, esto no significa que la memoria se recupera inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-495">Now, even though the rows in the tables have been deleted, this does not mean that memory is reclaimed immediately.</span></span> <span data-ttu-id="e2a87-496">SQL Server recupera memoria de las filas eliminadas de las tablas optimizadas para memoria en segundo plano, según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="e2a87-496">SQL Server reclaims memory from deleted rows in memory-optimized tables in the background, as needed.</span></span> <span data-ttu-id="e2a87-497">Verá que inmediatamente después de restablecer la demostración, sin ninguna carga de trabajo transaccional en el sistema, la memoria de las filas eliminadas aún no se ha recuperado:</span><span class="sxs-lookup"><span data-stu-id="e2a87-497">You will see that immediately after demo reset, with no transactional workload on the system, memory from deleted rows is not yet reclaimed:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-498">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="e2a87-498">**type**</span></span>|<span data-ttu-id="e2a87-499">**Nombre**</span><span class="sxs-lookup"><span data-stu-id="e2a87-499">**name**</span></span>|<span data-ttu-id="e2a87-500">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-500">**pages_MB**</span></span>|  
|<span data-ttu-id="e2a87-501">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-501">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-502">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-502">Default</span></span>|<span data-ttu-id="e2a87-503">2261</span><span class="sxs-lookup"><span data-stu-id="e2a87-503">2261</span></span>|  
|<span data-ttu-id="e2a87-504">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-504">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-505">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e2a87-505">DB_ID_5</span></span>|<span data-ttu-id="e2a87-506">7396</span><span class="sxs-lookup"><span data-stu-id="e2a87-506">7396</span></span>|  
|<span data-ttu-id="e2a87-507">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-507">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-508">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-508">Default</span></span>|<span data-ttu-id="e2a87-509">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-509">0</span></span>|  
|<span data-ttu-id="e2a87-510">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-510">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-511">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-511">Default</span></span>|<span data-ttu-id="e2a87-512">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-512">0</span></span>|  
  
 <span data-ttu-id="e2a87-513">Esto es lo esperado: la memoria se recuperará cuando se ejecute la carga de trabajo transaccional.</span><span class="sxs-lookup"><span data-stu-id="e2a87-513">This is expected: memory will be reclaimed when the transactional workload is running.</span></span>  
  
 <span data-ttu-id="e2a87-514">Si inicia una segunda ejecución de la carga de trabajo de demostración, verá que la utilización de memoria disminuye inicialmente, a medida que se limpian las filas eliminadas previamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-514">If you start a second run of the demo workload you will see the memory utilization decrease initially, as the previously deleted rows are cleaned up.</span></span> <span data-ttu-id="e2a87-515">En algún momento el tamaño de la memoria aumentará de nuevo, hasta que finalice la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-515">At some point the memory size will increase again, until the workload finishes.</span></span> <span data-ttu-id="e2a87-516">Después de insertar 10 millones de filas después de restablecer la demostración, el uso de memoria será muy similar al uso después de la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="e2a87-516">After inserting 10 million rows after demo reset, the memory utilization will be very similar to the utilization after the first run.</span></span> <span data-ttu-id="e2a87-517">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-517">For example:</span></span>  
  
```  
SELECT type  
, name  
, pages_kb/1024 AS pages_MB   
FROM sys.dm_os_memory_clerks WHERE type LIKE '%xtp%'  
```  
  
||||  
|-|-|-|  
|<span data-ttu-id="e2a87-518">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="e2a87-518">**type**</span></span>|<span data-ttu-id="e2a87-519">**Nombre**</span><span class="sxs-lookup"><span data-stu-id="e2a87-519">**name**</span></span>|<span data-ttu-id="e2a87-520">**pages_MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-520">**pages_MB**</span></span>|  
|<span data-ttu-id="e2a87-521">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-521">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-522">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-522">Default</span></span>|<span data-ttu-id="e2a87-523">1863</span><span class="sxs-lookup"><span data-stu-id="e2a87-523">1863</span></span>|  
|<span data-ttu-id="e2a87-524">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-524">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-525">DB_ID_5</span><span class="sxs-lookup"><span data-stu-id="e2a87-525">DB_ID_5</span></span>|<span data-ttu-id="e2a87-526">7390</span><span class="sxs-lookup"><span data-stu-id="e2a87-526">7390</span></span>|  
|<span data-ttu-id="e2a87-527">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-527">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-528">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-528">Default</span></span>|<span data-ttu-id="e2a87-529">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-529">0</span></span>|  
|<span data-ttu-id="e2a87-530">MEMORYCLERK_XTP</span><span class="sxs-lookup"><span data-stu-id="e2a87-530">MEMORYCLERK_XTP</span></span>|<span data-ttu-id="e2a87-531">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="e2a87-531">Default</span></span>|<span data-ttu-id="e2a87-532">0</span><span class="sxs-lookup"><span data-stu-id="e2a87-532">0</span></span>|  
  
### <a name="disk-utilization-for-memory-optimized-tables"></a><span data-ttu-id="e2a87-533">Uso de disco para las tablas optimizadas para memoria</span><span class="sxs-lookup"><span data-stu-id="e2a87-533">Disk utilization for memory-optimized tables</span></span>  
 <span data-ttu-id="e2a87-534">El tamaño total en disco de los archivos de punto de comprobación de una base de datos en un momento dado se puede averiguar con la consulta:</span><span class="sxs-lookup"><span data-stu-id="e2a87-534">The overall on-disk size for the checkpoint files of a database at a given time can be found using the query:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
  
```  
  
#### <a name="initial-state"></a><span data-ttu-id="e2a87-535">Estado inicial</span><span class="sxs-lookup"><span data-stu-id="e2a87-535">Initial state</span></span>  
 <span data-ttu-id="e2a87-536">Cuando se crean inicialmente el grupo de archivos de ejemplo y las tablas optimizadas para memoria de ejemplo, se crean previamente varios archivos de punto de comprobación y el sistema empieza a rellenar los archivos; el número de archivos de punto de comprobación creados previamente depende del número de procesadores lógicos del sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-536">When the sample filegroup and sample memory-optimized tables are created initially, a number of checkpoint files are pre-created and the system starts filling the files - the number of checkpoint files pre-created depends on the number of logical processors in the system.</span></span> <span data-ttu-id="e2a87-537">Como el ejemplo es inicialmente muy pequeño, los archivos creados previamente estarán vacíos en su mayoría después de la creación inicial.</span><span class="sxs-lookup"><span data-stu-id="e2a87-537">As the sample is initially very small, the pre-created files will be mostly empty after initial create.</span></span>  
  
 <span data-ttu-id="e2a87-538">A continuación se muestra el tamaño inicial en disco del ejemplo en un equipo con 16 procesadores lógicos:</span><span class="sxs-lookup"><span data-stu-id="e2a87-538">The following shows the initial on-disk size for the sample on a machine with 16 logical processors:</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e2a87-539">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-539">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e2a87-540">2312</span><span class="sxs-lookup"><span data-stu-id="e2a87-540">2312</span></span>|  
  
 <span data-ttu-id="e2a87-541">Como puede ver, hay una gran discrepancia entre el tamaño en disco de los archivos de punto de comprobación, que es 2,3 GB, y el tamaño de datos real, que es más cercano a 30 MB.</span><span class="sxs-lookup"><span data-stu-id="e2a87-541">As you can see, there is a big discrepancy between the on-disk size of the checkpoint files, which is 2.3GB, and the actual data size, which is closer to 30MB.</span></span>  
  
 <span data-ttu-id="e2a87-542">Para examinar más de cerca de dónde procede la utilización de espacio en disco, puede usar la consulta siguiente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-542">Looking closer at where the disk-space utilization comes from, you can use the following query.</span></span> <span data-ttu-id="e2a87-543">El tamaño del disco devuelto por esta consulta es aproximado en el caso de los archivos que tienen el estado 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE) o 7 (TOMBSTONE).</span><span class="sxs-lookup"><span data-stu-id="e2a87-543">The size on disk returned by this query is approximate for files with state in 5 (REQUIRED FOR BACKUP/HA), 6 (IN TRANSITION TO TOMBSTONE), or 7 (TOMBSTONE).</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
 <span data-ttu-id="e2a87-544">Para el estado inicial del ejemplo, el resultado será similar al de un servidor con 16 procesadores lógicos:</span><span class="sxs-lookup"><span data-stu-id="e2a87-544">For the initial state of the sample, the result will look something like for a server with 16 logical processors:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e2a87-545">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-545">**state_desc**</span></span>|<span data-ttu-id="e2a87-546">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-546">**file_type_desc**</span></span>|<span data-ttu-id="e2a87-547">**Recuento**</span><span class="sxs-lookup"><span data-stu-id="e2a87-547">**count**</span></span>|<span data-ttu-id="e2a87-548">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-548">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e2a87-549">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-549">PRECREATED</span></span>|<span data-ttu-id="e2a87-550">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-550">DATA</span></span>|<span data-ttu-id="e2a87-551">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-551">16</span></span>|<span data-ttu-id="e2a87-552">2048</span><span class="sxs-lookup"><span data-stu-id="e2a87-552">2048</span></span>|  
|<span data-ttu-id="e2a87-553">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-553">PRECREATED</span></span>|<span data-ttu-id="e2a87-554">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-554">DELTA</span></span>|<span data-ttu-id="e2a87-555">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-555">16</span></span>|<span data-ttu-id="e2a87-556">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-556">128</span></span>|  
|<span data-ttu-id="e2a87-557">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-557">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-558">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-558">DATA</span></span>|<span data-ttu-id="e2a87-559">1</span><span class="sxs-lookup"><span data-stu-id="e2a87-559">1</span></span>|<span data-ttu-id="e2a87-560">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-560">128</span></span>|  
|<span data-ttu-id="e2a87-561">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-561">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-562">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-562">DELTA</span></span>|<span data-ttu-id="e2a87-563">1</span><span class="sxs-lookup"><span data-stu-id="e2a87-563">1</span></span>|<span data-ttu-id="e2a87-564">8</span><span class="sxs-lookup"><span data-stu-id="e2a87-564">8</span></span>|  
  
 <span data-ttu-id="e2a87-565">Como puede ver, la mayor parte del espacio la usan archivos de datos y delta creados previamente.</span><span class="sxs-lookup"><span data-stu-id="e2a87-565">As you can see, most of the space is used by precreated data and delta files.</span></span> <span data-ttu-id="e2a87-566">SQL Server creó previamente un par de archivos (datos, delta) por procesador lógico.</span><span class="sxs-lookup"><span data-stu-id="e2a87-566">SQL Server pre-created one pair of (data, delta) files per logical processor.</span></span> <span data-ttu-id="e2a87-567">Además, los archivos de datos tienen un tamaño previo de 128 MB, y los archivos delta de 8 MB, para que la inserción de datos en estos archivos sea más eficaz.</span><span class="sxs-lookup"><span data-stu-id="e2a87-567">In addition, data files are pre-sized at 128MB, and delta files at 8MB, in order to make inserting data into these files more efficient.</span></span>  
  
 <span data-ttu-id="e2a87-568">Los datos reales de las tablas optimizadas para memoria están en el archivo de datos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-568">The actual data in the memory-optimized tables is in the single data file.</span></span>  
  
#### <a name="after-running-the-workload"></a><span data-ttu-id="e2a87-569">Después de ejecutar la carga de trabajo</span><span class="sxs-lookup"><span data-stu-id="e2a87-569">After running the workload</span></span>  
 <span data-ttu-id="e2a87-570">Después de una única serie de pruebas que inserta 10 millones de pedidos de venta, el tamaño total en disco es similar al siguiente (para un servidor de prueba de 16 núcleos):</span><span class="sxs-lookup"><span data-stu-id="e2a87-570">After a single test run that inserts 10 million sales orders, the overall on-disk size looks something like this (for a 16-core test server):</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e2a87-571">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-571">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e2a87-572">8828</span><span class="sxs-lookup"><span data-stu-id="e2a87-572">8828</span></span>|  
  
 <span data-ttu-id="e2a87-573">El tamaño en disco está cercano a 9 GB, que es parecido al tamaño en memoria de los datos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-573">The on-disk size is close to 9GB, which comes close to the in-memory size of the data.</span></span>  
  
 <span data-ttu-id="e2a87-574">Si examinamos más de cerca los tamaños de los archivos de punto de comprobación en los distintos estados:</span><span class="sxs-lookup"><span data-stu-id="e2a87-574">Looking more closely at the sizes of the checkpoint files across the various states:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e2a87-575">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-575">**state_desc**</span></span>|<span data-ttu-id="e2a87-576">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-576">**file_type_desc**</span></span>|<span data-ttu-id="e2a87-577">**Recuento**</span><span class="sxs-lookup"><span data-stu-id="e2a87-577">**count**</span></span>|<span data-ttu-id="e2a87-578">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-578">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e2a87-579">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-579">PRECREATED</span></span>|<span data-ttu-id="e2a87-580">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-580">DATA</span></span>|<span data-ttu-id="e2a87-581">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-581">16</span></span>|<span data-ttu-id="e2a87-582">2048</span><span class="sxs-lookup"><span data-stu-id="e2a87-582">2048</span></span>|  
|<span data-ttu-id="e2a87-583">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-583">PRECREATED</span></span>|<span data-ttu-id="e2a87-584">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-584">DELTA</span></span>|<span data-ttu-id="e2a87-585">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-585">16</span></span>|<span data-ttu-id="e2a87-586">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-586">128</span></span>|  
|<span data-ttu-id="e2a87-587">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-587">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-588">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-588">DATA</span></span>|<span data-ttu-id="e2a87-589">1</span><span class="sxs-lookup"><span data-stu-id="e2a87-589">1</span></span>|<span data-ttu-id="e2a87-590">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-590">128</span></span>|  
|<span data-ttu-id="e2a87-591">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-591">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-592">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-592">DELTA</span></span>|<span data-ttu-id="e2a87-593">1</span><span class="sxs-lookup"><span data-stu-id="e2a87-593">1</span></span>|<span data-ttu-id="e2a87-594">8</span><span class="sxs-lookup"><span data-stu-id="e2a87-594">8</span></span>|  
  
 <span data-ttu-id="e2a87-595">Todavía tenemos 16 pares de archivos creados previamente, listos a medida que se cierran los puntos de comprobación.</span><span class="sxs-lookup"><span data-stu-id="e2a87-595">We still have 16 pairs of pre-created files, ready to go as checkpoints are closed.</span></span>  
  
 <span data-ttu-id="e2a87-596">Hay un par en construcción, que se usa hasta que se cierra el punto de comprobación actual.</span><span class="sxs-lookup"><span data-stu-id="e2a87-596">There is one pair under construction, which is used until the current checkpoint is closed.</span></span> <span data-ttu-id="e2a87-597">Junto con los archivos de punto de comprobación activos, esto nos da unos 6,5 GB de uso de disco para 6,5 GB de datos en memoria.</span><span class="sxs-lookup"><span data-stu-id="e2a87-597">Along with the active checkpoint files this gives about 6.5GB of disk utilization for 6.5GB of data in memory.</span></span> <span data-ttu-id="e2a87-598">Recuerde que los índices no se conservan en disco, por lo que el tamaño total en disco es menor que el tamaño en memoria en este caso.</span><span class="sxs-lookup"><span data-stu-id="e2a87-598">Recall that indexes are not persisted on disk, and thus the overall size on disk is smaller than the size in memory in this case.</span></span>  
  
#### <a name="after-demo-reset"></a><span data-ttu-id="e2a87-599">Después de restablecer la demostración</span><span class="sxs-lookup"><span data-stu-id="e2a87-599">After demo reset</span></span>  
 <span data-ttu-id="e2a87-600">Después de restablecer la demostración, el espacio en disco no se recupera inmediatamente si no hay ninguna carga de trabajo transaccional en el sistema, y no hay ningún punto de comprobación de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="e2a87-600">After demo reset, disk space is not reclaimed immediately if there is no transactional workload on the system, and there are not database checkpoints.</span></span> <span data-ttu-id="e2a87-601">Para que los archivos de punto de comprobación pasen por sus diferentes etapas y después se descarten, tiene que haber varios puntos de comprobación y eventos de truncamiento del registro, con el fin de iniciar la combinación de los archivos de punto de comprobación e iniciar la recopilación de elementos no utilizados.</span><span class="sxs-lookup"><span data-stu-id="e2a87-601">For checkpoint files to be moved through their various stages and eventually be discarded, a number of checkpoints and log truncation events need to happen, to initiate merge of checkpoint files, as well as to initiate garbage collection.</span></span> <span data-ttu-id="e2a87-602">Estos ocurrirá automáticamente si tiene una carga de trabajo transaccional en el sistema [y realiza copias de seguridad de registros periódicas, en caso de que esté utilizando el modelo de recuperación completa], pero no cuando el sistema está inactivo, como ocurre en un escenario de demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-602">These will happen automatically if you have a transactional workload in the system [and take regular log backups, in case you are using the FULL recovery model], but not when the system is idle, as in a demo scenario.</span></span>  
  
 <span data-ttu-id="e2a87-603">En el ejemplo, después de restablecer la demostración, puede ver algo similar a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2a87-603">In the example, after demo reset, you may see something like</span></span>  
  
```  
SELECT SUM(df.size) * 8 / 1024 AS [On-disk size in MB]  
FROM sys.filegroups f JOIN sys.database_files df   
   ON f.data_space_id=df.data_space_id  
WHERE f.type=N'FX'  
```  
  
||  
|-|  
|<span data-ttu-id="e2a87-604">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-604">**On-disk size in MB**</span></span>|  
|<span data-ttu-id="e2a87-605">11839</span><span class="sxs-lookup"><span data-stu-id="e2a87-605">11839</span></span>|  
  
 <span data-ttu-id="e2a87-606">Con casi 12 GB, esto es mucho más significativo que los 9 GB teníamos antes de restablecer la demostración.</span><span class="sxs-lookup"><span data-stu-id="e2a87-606">At nearly 12GB, this is significantly more than the 9GB we had before the demo reset.</span></span> <span data-ttu-id="e2a87-607">Esto se debe a que se han iniciado algunas combinaciones de archivos de punto de comprobación, pero algunos destinos de mezcla todavía no se han instalado, y algunos de los archivos de origen de mezcla todavía no se han limpiado, como se puede ver aquí:</span><span class="sxs-lookup"><span data-stu-id="e2a87-607">This is because some checkpoint file merges have been started, but some of the merge targets have not yet been installed, and some of the merge source files have not yet been cleaned up, as can be seen from the following:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e2a87-608">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-608">**state_desc**</span></span>|<span data-ttu-id="e2a87-609">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-609">**file_type_desc**</span></span>|<span data-ttu-id="e2a87-610">**Recuento**</span><span class="sxs-lookup"><span data-stu-id="e2a87-610">**count**</span></span>|<span data-ttu-id="e2a87-611">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-611">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e2a87-612">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-612">PRECREATED</span></span>|<span data-ttu-id="e2a87-613">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-613">DATA</span></span>|<span data-ttu-id="e2a87-614">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-614">16</span></span>|<span data-ttu-id="e2a87-615">2048</span><span class="sxs-lookup"><span data-stu-id="e2a87-615">2048</span></span>|  
|<span data-ttu-id="e2a87-616">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-616">PRECREATED</span></span>|<span data-ttu-id="e2a87-617">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-617">DELTA</span></span>|<span data-ttu-id="e2a87-618">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-618">16</span></span>|<span data-ttu-id="e2a87-619">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-619">128</span></span>|  
|<span data-ttu-id="e2a87-620">ACTIVO</span><span class="sxs-lookup"><span data-stu-id="e2a87-620">ACTIVE</span></span>|<span data-ttu-id="e2a87-621">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-621">DATA</span></span>|<span data-ttu-id="e2a87-622">38</span><span class="sxs-lookup"><span data-stu-id="e2a87-622">38</span></span>|<span data-ttu-id="e2a87-623">5152</span><span class="sxs-lookup"><span data-stu-id="e2a87-623">5152</span></span>|  
|<span data-ttu-id="e2a87-624">ACTIVO</span><span class="sxs-lookup"><span data-stu-id="e2a87-624">ACTIVE</span></span>|<span data-ttu-id="e2a87-625">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-625">DELTA</span></span>|<span data-ttu-id="e2a87-626">38</span><span class="sxs-lookup"><span data-stu-id="e2a87-626">38</span></span>|<span data-ttu-id="e2a87-627">1331</span><span class="sxs-lookup"><span data-stu-id="e2a87-627">1331</span></span>|  
|<span data-ttu-id="e2a87-628">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="e2a87-628">MERGE TARGET</span></span>|<span data-ttu-id="e2a87-629">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-629">DATA</span></span>|<span data-ttu-id="e2a87-630">7</span><span class="sxs-lookup"><span data-stu-id="e2a87-630">7</span></span>|<span data-ttu-id="e2a87-631">896</span><span class="sxs-lookup"><span data-stu-id="e2a87-631">896</span></span>|  
|<span data-ttu-id="e2a87-632">MERGE TARGET</span><span class="sxs-lookup"><span data-stu-id="e2a87-632">MERGE TARGET</span></span>|<span data-ttu-id="e2a87-633">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-633">DELTA</span></span>|<span data-ttu-id="e2a87-634">7</span><span class="sxs-lookup"><span data-stu-id="e2a87-634">7</span></span>|<span data-ttu-id="e2a87-635">56</span><span class="sxs-lookup"><span data-stu-id="e2a87-635">56</span></span>|  
|<span data-ttu-id="e2a87-636">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="e2a87-636">MERGED SOURCE</span></span>|<span data-ttu-id="e2a87-637">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-637">DATA</span></span>|<span data-ttu-id="e2a87-638">13</span><span class="sxs-lookup"><span data-stu-id="e2a87-638">13</span></span>|<span data-ttu-id="e2a87-639">1772</span><span class="sxs-lookup"><span data-stu-id="e2a87-639">1772</span></span>|  
|<span data-ttu-id="e2a87-640">MERGED SOURCE</span><span class="sxs-lookup"><span data-stu-id="e2a87-640">MERGED SOURCE</span></span>|<span data-ttu-id="e2a87-641">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-641">DELTA</span></span>|<span data-ttu-id="e2a87-642">13</span><span class="sxs-lookup"><span data-stu-id="e2a87-642">13</span></span>|<span data-ttu-id="e2a87-643">455</span><span class="sxs-lookup"><span data-stu-id="e2a87-643">455</span></span>|  
  
 <span data-ttu-id="e2a87-644">Los destinos de mezcla se instalan y el origen de mezcla se limpia mientras la realiza actividad transaccional en el sistema.</span><span class="sxs-lookup"><span data-stu-id="e2a87-644">Merge targets are installed and merged source are cleaned up as transactional activity happens in the system.</span></span>  
  
 <span data-ttu-id="e2a87-645">Después de una segunda ejecución de la carga de trabajo de demostración, insertando 10 millones de pedidos de venta después de restablecer la demostración, verá que los archivos creados durante la primera ejecución de la carga de trabajo se han limpiado.</span><span class="sxs-lookup"><span data-stu-id="e2a87-645">After a second run of the demo workload, inserting 10 million sales orders after the demo reset, you will see that the files constructed during the first run of the workload have been cleaned up.</span></span> <span data-ttu-id="e2a87-646">Si ejecuta la consulta anterior varias veces mientras se está ejecutando la carga de trabajo, puede ver que los archivos de punto de comprobación pasaron por las distintas fases.</span><span class="sxs-lookup"><span data-stu-id="e2a87-646">If you run the above query several times while the workload is running, you can see the checkpoint files make their way through the various stages.</span></span>  
  
 <span data-ttu-id="e2a87-647">Después de que la segunda ejecución de la carga de trabajo inserta 10 millones de pedidos de venta, verá un uso de disco muy similar, aunque no necesariamente igual después de la primera ejecución, porque el sistema es dinámico por naturaleza.</span><span class="sxs-lookup"><span data-stu-id="e2a87-647">After the second run of the workload insert 10 million sales orders you will see disk utilization very similar to, though not necessarily the same as after the first run, as the system is dynamic in nature.</span></span> <span data-ttu-id="e2a87-648">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2a87-648">For example:</span></span>  
  
```  
SELECT state_desc  
 , file_type_desc  
 , COUNT(*) AS [count]  
 , SUM(CASE  
   WHEN state = 5 AND file_type=0 THEN 128*1024*1024  
   WHEN state = 5 AND file_type=1 THEN 8*1024*1024  
   WHEN state IN (6,7) THEN 68*1024*1024  
   ELSE file_size_in_bytes  
    END) / 1024 / 1024 AS [on-disk size MB]   
FROM sys.dm_db_xtp_checkpoint_files  
GROUP BY state, state_desc, file_type, file_type_desc  
ORDER BY state, file_type  
```  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="e2a87-649">**state_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-649">**state_desc**</span></span>|<span data-ttu-id="e2a87-650">**file_type_desc**</span><span class="sxs-lookup"><span data-stu-id="e2a87-650">**file_type_desc**</span></span>|<span data-ttu-id="e2a87-651">**Recuento**</span><span class="sxs-lookup"><span data-stu-id="e2a87-651">**count**</span></span>|<span data-ttu-id="e2a87-652">**Tamaño en disco en MB**</span><span class="sxs-lookup"><span data-stu-id="e2a87-652">**on-disk size MB**</span></span>|  
|<span data-ttu-id="e2a87-653">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-653">PRECREATED</span></span>|<span data-ttu-id="e2a87-654">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-654">DATA</span></span>|<span data-ttu-id="e2a87-655">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-655">16</span></span>|<span data-ttu-id="e2a87-656">2048</span><span class="sxs-lookup"><span data-stu-id="e2a87-656">2048</span></span>|  
|<span data-ttu-id="e2a87-657">PRECREATED</span><span class="sxs-lookup"><span data-stu-id="e2a87-657">PRECREATED</span></span>|<span data-ttu-id="e2a87-658">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-658">DELTA</span></span>|<span data-ttu-id="e2a87-659">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-659">16</span></span>|<span data-ttu-id="e2a87-660">128</span><span class="sxs-lookup"><span data-stu-id="e2a87-660">128</span></span>|  
|<span data-ttu-id="e2a87-661">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-661">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-662">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-662">DATA</span></span>|<span data-ttu-id="e2a87-663">2</span><span class="sxs-lookup"><span data-stu-id="e2a87-663">2</span></span>|<span data-ttu-id="e2a87-664">268</span><span class="sxs-lookup"><span data-stu-id="e2a87-664">268</span></span>|  
|<span data-ttu-id="e2a87-665">UNDER CONSTRUCTION</span><span class="sxs-lookup"><span data-stu-id="e2a87-665">UNDER CONSTRUCTION</span></span>|<span data-ttu-id="e2a87-666">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-666">DELTA</span></span>|<span data-ttu-id="e2a87-667">2</span><span class="sxs-lookup"><span data-stu-id="e2a87-667">2</span></span>|<span data-ttu-id="e2a87-668">16</span><span class="sxs-lookup"><span data-stu-id="e2a87-668">16</span></span>|  
|<span data-ttu-id="e2a87-669">ACTIVO</span><span class="sxs-lookup"><span data-stu-id="e2a87-669">ACTIVE</span></span>|<span data-ttu-id="e2a87-670">DATA</span><span class="sxs-lookup"><span data-stu-id="e2a87-670">DATA</span></span>|<span data-ttu-id="e2a87-671">41</span><span class="sxs-lookup"><span data-stu-id="e2a87-671">41</span></span>|<span data-ttu-id="e2a87-672">5608</span><span class="sxs-lookup"><span data-stu-id="e2a87-672">5608</span></span>|  
|<span data-ttu-id="e2a87-673">ACTIVO</span><span class="sxs-lookup"><span data-stu-id="e2a87-673">ACTIVE</span></span>|<span data-ttu-id="e2a87-674">DELTA</span><span class="sxs-lookup"><span data-stu-id="e2a87-674">DELTA</span></span>|<span data-ttu-id="e2a87-675">41</span><span class="sxs-lookup"><span data-stu-id="e2a87-675">41</span></span>|<span data-ttu-id="e2a87-676">328</span><span class="sxs-lookup"><span data-stu-id="e2a87-676">328</span></span>|  
  
 <span data-ttu-id="e2a87-677">En este caso, hay dos pares de archivos de punto de comprobación en el estado "under construction", lo que significa que varios pares de archivos pasaron por el estado "under construction", probablemente debido al elevado nivel de simultaneidad de la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e2a87-677">In this case, there are two checkpoint file pairs in the 'under construction' state, which means multiple file pairs were moved to the 'under construction' state, likely due to the high level of concurrency in the workload.</span></span> <span data-ttu-id="e2a87-678">Varios subprocesos simultáneos necesitaron un nuevo par de archivos al mismo tiempo, por lo que se movió un par de "precreated" a "under construction".</span><span class="sxs-lookup"><span data-stu-id="e2a87-678">Multiple concurrent threads required a new file pair at the same time, and thus moved a pair from 'precreated' to 'under construction'.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a87-679">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e2a87-679">See Also</span></span>  
 [<span data-ttu-id="e2a87-680">OLTP en memoria &#40;optimización en memoria&#41;</span><span class="sxs-lookup"><span data-stu-id="e2a87-680">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)