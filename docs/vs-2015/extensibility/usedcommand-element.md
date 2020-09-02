---
title: Elemento UsedCommand | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91929038d77bcf14c6997f9b60551ed8c9c3b820
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186371"
---
# <a name="usedcommand-element"></a>Elemento UsedCommand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Consente a un VSPackage di accedere a un comando definito in un altro file con estensione vsct. Se, ad esempio, il pacchetto VSPackage usa il comando **Copy** standard, definito dalla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Shell, è possibile aggiungere il comando a un menu o a una barra degli strumenti senza implementarlo di nuovo.  
  
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
  
## <a name="remarks"></a>Osservazioni  
 Aggiungendo un comando all' `<UsedCommands>` elemento, un VSPackage informa l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente che il pacchetto VSPackage richiede il comando. È necessario aggiungere un `<UsedCommand>` elemento per qualsiasi comando richiesto dal pacchetto che potrebbe non essere incluso in tutte le versioni e le configurazioni di Visual Studio. Se, ad esempio, il pacchetto chiama un comando specifico per Visual C++, il comando non sarà disponibile per gli utenti di Visual Web Developer a meno che non si includa un `<UsedCommand>` elemento per il comando.  
  
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
 [File Visual Studio Command Table (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
