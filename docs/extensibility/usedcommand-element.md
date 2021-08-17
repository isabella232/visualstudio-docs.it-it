---
title: Elemento UsedCommand | Microsoft Docs
description: L'elemento UsedCommand consente a un VSPackage di accedere a un comando definito in un altro file con estensione vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0333b3a83333eebdb25da83206b9da2a4c9082ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049285"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un VSPackage di accedere a un comando definito in un altro file con estensione vsct. Ad esempio, se il pacchetto VSPackage usa il comando **Copia** standard, definito dalla shell, è possibile aggiungere il comando a un menu o a una barra degli strumenti senza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementarlo di nuovo.

## <a name="syntax"></a>Sintassi

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID della coppia ID GUID che identifica il comando.|
|id|Obbligatorio. ID della coppia ID GUID che identifica il comando.|
|Condition|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.|

## <a name="remarks"></a>Commenti
 Aggiungendo un comando all'elemento `<UsedCommands>` , un pacchetto VSPackage informa l'ambiente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che il pacchetto VSPackage richiede il comando . È necessario aggiungere un elemento per qualsiasi comando richiesto dal pacchetto che potrebbe non essere incluso in tutte le versioni e le configurazioni `<UsedCommand>` di Visual Studio. Ad esempio, se il pacchetto chiama un comando specifico di Visual C++, il comando non sarà disponibile per gli utenti di Visual Web Developer, a meno che non si includa un elemento per `<UsedCommand>` il comando.

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
- [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
