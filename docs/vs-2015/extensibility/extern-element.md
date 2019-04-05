---
title: Elemento extern | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17477b7eb60aa332f6910019e28f4c53aa31ebf1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968177"
---
# <a name="extern-element"></a>Elemento Extern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'elemento Extern fa riferimento a qualsiasi file di intestazione esterno (con estensione h) di tipo merge con il file con estensione vsct in fase di compilazione. I file da unire devono trovarsi nel percorso di inclusione specificato per il compilatore VSCT oppure fa riferimento un' [elemento includono](../extensibility/include-element.md). I file potrebbero essere altri file con estensione vsct o file di intestazione C++.  
  
 Le definizioni nel file di intestazione devono essere nel formato "#define [simbolo] [valore]" il valore può essere un altro simbolo, se è definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali di elementi di comando. Qualsiasi simbolo non usato effettivamente verrà rimosse.  
  
 Elemento CommandTable  
Elemento Extern  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Il percorso del file di intestazione:<br /><br /> href="stdidcmd.h"|  
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|language|Facoltativo. La lingua predefinita di tutte le [ \<stringhe >](../extensibility/strings-element.md) elementi della tabella comandi:<br /><br /> language="en-us"|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, vale a dire, voci di menu, menu, barre degli strumenti e caselle combinate, ovvero che un pacchetto VSPackage fornisce all'IDE.|  
  
## <a name="example"></a>Esempio  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    …  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
