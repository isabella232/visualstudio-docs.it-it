---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718780"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un VSPackage di accedere a un comando definito in un altro file con estensione vsct. Se, ad esempio, il pacchetto VSPackage usa il comando **Copy** standard, definito dalla shell di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile aggiungere il comando a un menu o a una barra degli strumenti senza implementarlo di nuovo.

## <a name="syntax"></a>Sintassi

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID della coppia GUID ID che identifica il comando.|
|ID|Obbligatorio. ID della coppia GUID ID che identifica il comando.|
|Condizione|Parametro facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Nessuno||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.|

## <a name="remarks"></a>Note
 Aggiungendo un comando all'elemento `<UsedCommands>`, un VSPackage informa l'ambiente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che il pacchetto VSPackage richiede il comando. È necessario aggiungere un elemento `<UsedCommand>` per tutti i comandi richiesti dal pacchetto che potrebbero non essere inclusi in tutte le versioni e le configurazioni di Visual Studio. Se, ad esempio, il pacchetto chiama un comando specifico per l'oggetto C++visivo, il comando non sarà disponibile per gli utenti di Visual Web Developer, a meno che non si includa un elemento `<UsedCommand>` per il comando.

## <a name="example"></a>Esempio

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Vedere anche
- [Elemento UsedCommands](../extensibility/usedcommands-element.md)
- [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)