---
title: Configurazione di visualizzazione della finestra degli strumenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186400"
---
# <a name="tool-window-display-configuration"></a>Configurazione della visualizzazione della finestra degli strumenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando un pacchetto VSPackage registra una finestra degli strumenti, la posizione predefinita, le dimensioni, lo stile di ancoraggio e altre informazioni sulla visibilità sono specificate in valori facoltativi. Per ulteriori informazioni sulla registrazione della finestra degli strumenti, vedere la pagina relativa alle [finestre degli strumenti nel registro di sistema](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informazioni visualizzate finestra  
 La configurazione di base dello schermo di una finestra degli strumenti viene archiviata fino a sei valori facoltativi:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|Nome|REG_SZ|"Nome breve|Nome breve che descrive la finestra degli strumenti. Utilizzato solo per riferimento nel registro di sistema.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Quattro valori delimitati da virgole. X1, Y1 è la coordinata dell'angolo superiore sinistro della finestra degli strumenti. X2, Y2 è la coordinata dell'angolo inferiore destro. Tutti i valori sono nelle coordinate dello schermo.|  
|Stile|REG_SZ|MDI<br /><br /> Float<br /><br /> Collegato<br /><br /> A schede<br /><br /> "AlwaysFloat"|Parola chiave che specifica lo stato di visualizzazione iniziale della finestra degli strumenti.<br /><br /> "MDI" = ancorato con la finestra MDI.<br /><br /> "Float" = Floating.<br /><br /> "Linked" = collegata a un'altra finestra (specificata nella voce della finestra).<br /><br /> "A schede" = combinato con un'altra finestra degli strumenti.<br /><br /> "AlwaysFloat" = non può essere ancorato.<br /><br /> Per ulteriori informazioni, vedere la sezione dei commenti riportata di seguito.|  
|Finestra|REG_SZ|*\<GUID>*|GUID di una finestra a cui è possibile collegare o a schede la finestra degli strumenti. Il GUID può appartenere a una delle finestre personali o a una delle finestre nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientamento|REG_SZ|Sinistra<br /><br /> Destra<br /><br /> Top<br /><br /> Parte inferiore|Vedere la sezione dei commenti riportata di seguito.|  
|DontForceCreate|REG_DWORD|0 o 1|Quando questa voce è presente e il valore è diverso da zero, la finestra viene caricata, ma non immediatamente visualizzata.|  
  
### <a name="comments"></a>Commenti  
 La voce orientamento definisce la posizione di ancoraggio della finestra degli strumenti quando si fa doppio clic sulla barra del titolo. La posizione è relativa alla finestra specificata nella voce della finestra. Se la voce di stile è impostata su "Linked", la voce di orientamento può essere "left", "Right", "Top" o "bottom". Se la voce di stile è "a schede", la voce di orientamento può essere "left" o "Right" e specificare dove viene aggiunta la scheda. Se la voce di stile è "float", la finestra degli strumenti viene spostata per prima. Quando si fa doppio clic sulla barra del titolo, si applicano le voci relative all'orientamento e alla finestra e la finestra usa lo stile "a schede". Se la voce di stile è "AlwaysFloat", la finestra degli strumenti non può essere ancorata. Se la voce di stile è "MDI", la finestra degli strumenti è collegata all'area MDI e la voce della finestra viene ignorata.  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilità della finestra degli strumenti  
 I valori nella sottochiave di visibilità facoltativa determinano le impostazioni di visibilità di una finestra degli strumenti. I nomi dei valori vengono usati per archiviare i GUID dei comandi che richiedono la visibilità della finestra. Se il comando viene eseguito, l'IDE garantisce che la finestra degli strumenti venga creata e resa visibile.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|Valore predefinito.|REG_SZ|Nessuno|Lasciare vuoto.|  
|*\<GUID>*|REG_DWORD o REG_SZ|0 o una stringa descrittiva.|facoltativo. Il nome della voce deve essere il GUID di un comando che richiede visibilità. Il valore include solo una stringa informativa. In genere, il valore è `reg_dword` impostato su 0.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di base sui VSPackage](../misc/vspackage-essentials.md)
