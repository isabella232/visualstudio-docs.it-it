---
title: Parametri di modello | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef4e1a6e3c56df744ce5375a1cb3a1dbd53a6fad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238901"
---
# <a name="template-parameters"></a>Parametri di template
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilizzando i parametri nei modelli, è possibile sostituire i valori di parti di chiavi del modello, ad esempio i nomi delle classi e degli spazi dei nomi, quando viene creata un'istanza del modello. Questi parametri vengono sostituiti dalla procedura guidata di creazione modelli eseguita in background quando un utente fa clic su **OK** nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.  
  
## <a name="declaring-and-enabling-template-parameters"></a>Dichiarazione e abilitazione dei parametri di modello  
 I parametri di modello vengono dichiarati nel formato $*parametro*$. Ad esempio:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### <a name="to-enable-parameter-substitution-in-templates"></a>Per abilitare la sostituzione dei parametri nei modelli  
  
1.  Nel file .vstemplate del modello individuare l'elemento `ProjectItem` che corrisponde all'elemento per il quale si desidera attivare la sostituzione dei parametri.  
  
2.  Impostare l'attributo `ReplaceParameters` dell'elemento `ProjectItem` su `true`.  
  
3.  Includere i parametri nella posizione appropriata nel file di codice per l'elemento del progetto. Ad esempio, il parametro seguente specifica che deve essere usato il nome di progetto sicuro per lo spazio dei nomi in un file:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## <a name="reserved-template-parameters"></a>Parametri di modello riservati  
 Nella tabella seguente sono elencati i parametri di modello riservati che possono essere usati da qualsiasi modello.  
  
> [!NOTE]
>  I parametri di modello fanno distinzione tra maiuscole e minuscole.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`clrversion`|Versione corrente di Common Language Runtime (CLR).|  
|`GUID [1-10]`|GUID usato per sostituire il GUID del progetto in un file di progetto. È possibile specificare fino a 10 GUID univoci, ad esempio `guid1)`.|  
|`itemname`|Nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.|  
|`machinename`|Nome del computer corrente, ad esempio Computer01.|  
|`projectname`|Nome specificato dall'utente nella finestra di dialogo **Nuovo progetto**.|  
|`registeredorganization`|Valore della chiave del Registro di sistema da HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|  
|`rootnamespace`|Spazio dei nomi radice del progetto corrente. Questo parametro è valido solo per i modelli di elemento.|  
|`safeitemname`|Nome specificato dall'utente nella finestra di dialogo **Aggiungi nuovo elemento** con tutti i caratteri non sicuri e gli spazi rimossi.|  
|`safeprojectname`|Nome specificato dall'utente nella finestra di dialogo **Nuovo progetto** con tutti i caratteri non sicuri e gli spazi rimossi.|  
|`time`|L'ora corrente nel formato GG/MM/AAAA 00:00:00.|  
|`SpecificSolutionName`|Nome della soluzione. Quando l'opzione per creare una directory di soluzione è selezionata, `SpecificSolutionName` è il nome della soluzione. Quando l'opzione per creare una directory di soluzione non è selezionata, `SpecificSolutionName` è vuoto.|  
|`userdomain`|Dominio dell'utente corrente.|  
|`username`|Nome dell'utente corrente.|  
|`webnamespace`|Nome del sito Web corrente. Questo parametro viene usato nel modello di modulo Web per garantire che i nomi delle classi siano univoci. Se il sito Web si trova nella directory radice del server Web, questo parametro di modello si risolve nella directory radice del server Web.|  
|`year`|L'anno corrente nel formato AAAA.|  
  
## <a name="custom-template-parameters"></a>Parametri di modello personalizzati  
 Oltre ai parametri di modello riservati predefiniti usati per la sostituzione dei parametri, è possibile specificare i propri valori e parametri di modello. Per altre informazioni, vedere [Elemento CustomParameters (modelli di Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## <a name="example-replacing-files-names"></a>Esempio: sostituzione di nomi di file  
 È possibile specificare nomi di file variabili per gli elementi del progetto usando un parametro con l'attributo `TargetFileName`. Ad esempio, è possibile specificare che il file EXE usi il nome del progetto, specificato da `$projectname$`, come nome del file.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## <a name="example-using-the-project-name-for-the-namespace-name"></a>Esempio: uso del nome del progetto per il nome dello spazio dei nomi  
 Per usare il nome del progetto per lo spazio dei nomi in un file di classe di Visual C#, Class1.cs, usare la sintassi seguente:  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 Nel file VSTEMPLATE del modello di progetto, includere il seguente codice XML quando si fa riferimento al file Class1.cs:  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)



