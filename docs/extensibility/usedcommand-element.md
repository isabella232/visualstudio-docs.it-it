---
title: UsedCommand (elemento) . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698831"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un pacchetto VSPackage di accedere a un comando definito in un altro file vsct. Ad esempio, se il pacchetto VSPackage utilizza il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando **standard Copia,** che è definito dalla shell, è possibile aggiungere il comando a un menu o barra degli strumenti senza implementarlo nuovamente.

## <a name="syntax"></a>Sintassi

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|guid|Obbligatorio. GUID della coppia di ID GUID che identifica il comando.|
|id|Obbligatorio. ID della coppia di ID GUID che identifica il comando.|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|nessuno||

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Gruppi UsedCommand elementi e altri UsedCommands raggruppamenti.|

## <a name="remarks"></a>Osservazioni
 Aggiungendo un comando `<UsedCommands>` all'elemento, un VSPackage informa l'ambiente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che il pacchetto VSPackage richiede il comando. È necessario `<UsedCommand>` aggiungere un elemento per qualsiasi comando il pacchetto richiede che potrebbe non essere incluso in tutte le versioni e configurazioni di Visual Studio.You should add a element for any command your package requires that might not be included in all versions and configurations of Visual Studio. Se, ad esempio, il pacchetto chiama un comando specifico di Visual C, il comando non sarà `<UsedCommand>` disponibile per gli utenti di Visual Web Developer a meno che non si includa un elemento per il comando.

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
