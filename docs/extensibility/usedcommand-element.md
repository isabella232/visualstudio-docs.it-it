---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ccc96d92e83ea42c6921abd2159499c1e9c42c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930355"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
Consente a un VSPackage di accedere a un comando che viene definito in un altro file con estensione vsct. Ad esempio, se il pacchetto VSPackage Usa lo standard **copia** comando, che è definito dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, può aggiungere il comando a un menu o sulla barra degli strumenti senza implementarla nuovamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. Il GUID della coppia ID GUID che identifica il comando.|  
|ID|Obbligatorio. L'ID della coppia ID GUID che identifica il comando.|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.|  
  
## <a name="remarks"></a>Note  
 Tramite l'aggiunta di un comando per il `<UsedCommands>` elemento, un pacchetto VSPackage informa il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente che il pacchetto VSPackage richiede che il comando. È consigliabile aggiungere un `<UsedCommand>` (elemento) per qualsiasi comando richiesto dal pacchetto che potrebbe non essere inclusi in tutte le versioni e le configurazioni di Visual Studio. Ad esempio, se il pacchetto chiama un comando specifico di Visual C++, il comando non non sarà disponibile per gli utenti di Visual Web Developer a meno che non si include un `<UsedCommand>` (elemento) per il comando.  
  
## <a name="example"></a>Esempio  
  
```  
<UsedCommands>  
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>  
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>  
</UsedCommands>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)