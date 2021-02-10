---
title: Elemento UsedCommand | Microsoft Docs
description: L'elemento UsedCommand consente a un VSPackage di accedere a un comando definito in un altro file. vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c3f4a5f39e7cb999d9b3a86aa791464fca25645
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934103"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un VSPackage di accedere a un comando definito in un altro file con estensione vsct. Se, ad esempio, il pacchetto VSPackage usa il comando **Copy** standard, definito dalla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell, è possibile aggiungere il comando a un menu o a una barra degli strumenti senza implementarlo di nuovo.

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
|id|Obbligatorio. ID della coppia GUID ID che identifica il comando.|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.|

## <a name="remarks"></a>Commenti
 Aggiungendo un comando all' `<UsedCommands>` elemento, un VSPackage informa l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente che il pacchetto VSPackage richiede il comando. È necessario aggiungere un `<UsedCommand>` elemento per qualsiasi comando richiesto dal pacchetto che potrebbe non essere incluso in tutte le versioni e le configurazioni di Visual Studio. Se, ad esempio, il pacchetto chiama un comando specifico per Visual C++, il comando non sarà disponibile per gli utenti di Visual Web Developer a meno che non si includa un `<UsedCommand>` elemento per il comando.

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
