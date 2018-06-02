---
title: Batch-Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4644b8775212eae0cb6d912df9bc415c5fc96ec7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34573942"
---
# <a name="batch-element-xmla"></a>Batch-Element (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Führt eine oder mehrere XML für Analysis (XMLA) Befehle als Batchvorgang, sequenziell oder parallel auf einer Instanz von Analysis Services.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <Batch Transaction="Boolean" ProcessAffectedObjects="Boolean">  
      <Bindings>...</Bindings>  
      <DataSource>...</DataSource>  
      <DataSourceView>...</DataSourceView>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <Parallel>...</Parallel>  
      <!-- One or more XMLA commands -->  
   </Batch>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Bindungen](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md), [DataSource](../../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md), [DataSourceView](../../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md), [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md), [Parallel](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)<br /><br /> Eine oder mehrere der folgenden XMLA-Befehle: [Alter](../../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md), [Sicherung](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [ClearCache](../../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md), [ CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), [erstellen](../../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md), [löschen](../../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md), [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md), [löschen](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md), [Einfügen](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md), [Sperre](../../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md), [MergePartitions](../../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md), [NotifyTableChange](../../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md), [Prozess](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md), [Wiederherstellen](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md), [RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md), [SetPasswordEncryptionKey](http://msdn.microsoft.com/en-us/fb262737-f0f4-4441-985e-3b2a94d00a9e), [Anweisung](../../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md), [Abonnieren](../../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md), [Synchronisieren](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md), [Entsperren](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md), [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md), [UpdateCells](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)|  
  
## <a name="attributes"></a>Attribute  
  
|attribute|Description|  
|---------------|-----------------|  
|ProcessAffectedObjects|(Optionales **Boolean** -Attribut) Gibt an, ob alle Objekte, die eine Wiederverarbeitung erfordern, verarbeitet werden.<br /><br /> Wenn auf True festgelegt, die [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz verarbeitet alle Objekte, die erforderlich ist, eine erneute Verarbeitung als Ergebnis der Verarbeitung eines Objekts in der **Batch** Befehl.<br /><br /> Wenn auf festgelegt **"false"**, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz verarbeitet nur die Objekte, die in enthalten die **Batch** Befehl.|  
|Transaction|(Optionales **Boolean** -Attribut) Gibt an, ob der im **Batch** -Befehl enthaltene Befehl als eine einzelne Transaktion oder als individuelle Transaktionen behandelt wird.<br /><br /> Wenn er auf "True" gesetzt ist, gelten alle im **Batch** -Befehl enthaltenen Befehle als eine einzelne Transaktion. Wenn einer der Befehle fehlschlägt, findet für alle Befehle, die vor dem fehlgeschlagenen Befehl ausgeführt wurden, ein Rollback statt und der **Batch** -Befehl wird angehalten, ohne die folgenden Befehle auszuführen.<br /><br /> Wenn der **false**-Befehl auf **Batch** festgelegt ist, wird versucht, jeden Befehl auszuführen. Anschließend wird für die Ergebnisse jedes Befehls, der erfolgreich abgeschlossen wurde, ein Commit ausgeführt.|  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]  
>  Command/Execute/Statement wird in einem Batchvorgang derzeit nicht unterstützt.  
  
 Weitere Informationen zum Durchführen von Batchvorgängen in XMLA finden Sie unter [Durchführen von Batchvorgängen &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/performing-batch-operations-xmla.md).  
  
## <a name="see-also"></a>Siehe auch
 [Befehle &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
