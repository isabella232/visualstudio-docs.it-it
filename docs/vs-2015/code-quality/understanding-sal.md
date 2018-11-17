---
title: La comprensione SAL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 712d99f3839982632e54b622b3512eb611f2bf95
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792816"
---
# <a name="understanding-sal"></a>Informazioni su SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Linguaggio di annotazione del codice sorgente Microsoft (SAL) fornisce un set di annotazioni che è possibile utilizzare per descrivere come una funzione utilizza le garanzie che questa mette al termine, i relativi parametri e i presupposti che questa mette bloccarli. Le annotazioni sono definite nel file di intestazione `<sal.h>`. Analisi di codice di Visual Studio per C++ Usa le annotazioni SAL per modificare l'analisi delle funzioni. Per altre informazioni su SAL 2.0 per lo sviluppo di driver di Windows, vedere [SAL 2.0 di annotazioni per Windows i driver](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 In modo nativo, C e C++ forniscono solo alcune modalità per gli sviluppatori di esprimere in modo coerente con finalità e l'invarianza. Utilizzando le annotazioni SAL, è possibile descrivere le funzioni più dettagliatamente in modo che gli sviluppatori che li usano più facilmente comprensibili come usarli.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>What ' s SAL e il motivo per cui è opportuno utilizzarla?  
 Semplificando, SAL è una soluzione economica per consentire al compilatore di controllare il codice per l'utente.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL rende di codice più utili  
 SAL può aiutarti a rendere la progettazione di codice più comprensibile sia per gli essere umani per strumenti di analisi codice. Si consideri l'esempio che mostra la funzione di runtime C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 È possibile conoscere ciò che svolge questa funzione? Quando una funzione è implementata o chiamata, è necessario mantenere alcune proprietà per garantire la correttezza del programma. Osservando semplicemente una dichiarazione come quello nell'esempio, non si conosce quali siano. Senza annotazioni SAL, è necessario fare affidamento sulla documentazione o commenti del codice. Ecco quali la documentazione di MSDN per `memcpy` afferma:  
  
> "Copie contano i byte di src a dest. Se l'origine e destinazione si sovrappongono, il comportamento di memcpy è definito. Usare memmove per gestire le aree di sovrapposizione.   
> **Nota sulla sicurezza:** assicurarsi che il buffer di destinazione sia della stessa dimensione o maggiore del buffer di origine. Per altre informazioni, vedere evitare sovraccarichi del Buffer".  
  
 La documentazione contiene un paio di bit di informazioni che suggeriscono che il codice deve gestire alcune proprietà per garantire la correttezza del programma:  
  
- `memcpy` copie di `count` di byte dal buffer di origine nel buffer di destinazione.  
  
- Il buffer di destinazione debba essere uguali almeno alle dimensioni del buffer di origine.  
  
  Tuttavia, il compilatore non è possibile leggere la documentazione o commenti informali. Non è chiaro che vi sia una relazione tra due buffer e `count`, inoltre non è possibile in modo efficace indovinare su una relazione. SAL può fornire maggiore chiarezza sulle proprietà e implementazione della funzione, come illustrato di seguito:  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Si noti che queste annotazioni simile alle informazioni nella documentazione di MSDN, ma sono più concise e seguono un modello semantico. Quando si legge questo codice, è possibile comprendere rapidamente le proprietà di questa funzione e come evitare problemi di sicurezza di sovraccarico del buffer. Ancora meglio, i modelli semantici che fornisce SAL possono migliorare l'efficienza e l'efficacia degli strumenti di analisi codice automatica l'individuazione iniziali di potenziali bug. Si supponga che un utente scrive questa implementazione difettoso di `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Questa implementazione contiene un errore comune off alla volta. Per fortuna, l'autore di codice inclusi annotazione SAL buffer delle dimensioni, ovvero uno strumento di analisi codice può intercettare il bug grazie all'analisi di questa funzione solo.  
  
### <a name="sal-basics"></a>Nozioni di base SAL  
 SAL definisce quattro tipi base di parametri, che vengono classificati in base al modello di utilizzo.  
  
|Category|Annotazione parametro|Descrizione|  
|--------------|--------------------------|-----------------|  
|**Input alla chiamata alla funzione**|`_In_`|I dati viene passati alla funzione chiamata e viene considerati di sola lettura.|  
|**Input alla chiamata alla funzione e di output al chiamante**|`_Inout_`|Dati utilizzabili siano passati alla funzione e potenzialmente viene modificati.|  
|**Output al chiamante**|`_Out_`|Il chiamante fornisce solo lo spazio per la funzione chiamata in cui scrivere. La funzione chiamata scrive i dati in tale spazio.|  
|**Output del puntatore al chiamante**|`_Outptr_`|Ad esempio **di Output al chiamante**. Il valore restituito dalla funzione chiamata è un puntatore.|  
  
 Queste quattro annotazioni di base possono essere reso più esplicite in vari modi. Per impostazione predefinita, i parametri di puntatore con annotazioni si presuppone che siano necessari, ovvero devono essere non NULL per la funzione abbia esito positivo. Le variazioni di uso più frequente delle annotazioni di base indica che un parametro del puntatore è facoltativo, ovvero se è NULL, la funzione può comunque eseguita in modo.  
  
 Questa tabella mostra come distinguere tra i parametri obbligatori e facoltativi:  
  
||I parametri sono obbligatori|I parametri sono facoltativi|  
|-|-----------------------------|-----------------------------|  
|**Input alla chiamata alla funzione**|`_In_`|`_In_opt_`|  
|**Input alla chiamata alla funzione e di output al chiamante**|`_Inout_`|`_Inout_opt_`|  
|**Output al chiamante**|`_Out_`|`_Out_opt_`|  
|**Output del puntatore al chiamante**|`_Outptr_`|`_Outptr_opt_`|  
  
 Queste annotazioni aiutano a identificare i possibili valori non inizializzati e un puntatore null non valido viene utilizzato in modo formale e accurato. Passaggio di NULL a un parametro obbligatorio potrebbe causare un arresto anomalo del sistema, o potrebbe causare un codice di errore "non riuscito" deve essere restituito. In entrambi i casi, la funzione non può avere esito positivo di svolgere il proprio lavoro.  
  
## <a name="sal-examples"></a>Esempi SAL  
 In questa sezione vengono illustrati esempi di codice per le annotazioni SAL base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Usando lo strumento di analisi codice di Visual Studio per individuare i difetti  
 Negli esempi viene utilizzato lo strumento di analisi del codice di Visual Studio con le annotazioni SAL per individuare i difetti del codice. Di seguito viene illustrato come eseguire questa operazione.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Usare gli strumenti di analisi codice di Visual Studio e SAL  
  
1. In Visual Studio, aprire un progetto C++ che contiene le annotazioni SAL.  
  
2. Nella barra dei menu, scegliere **compilare**, **Esegui analisi del codice sulla soluzione**.  
  
    Prendere in considerazione la \_In\_ riportato in questa sezione. Se si esegue l'analisi del codice su di esso, viene visualizzato questo avviso:  
  
   > **C6387 Valore di parametro non valido**   
   > 'pInt' potrebbe essere '0': questa condizione non soddisfa la specifica la funzione 'InCallee'.  
  
### <a name="example-the-in-annotation"></a>Esempio: La \_In\_ annotazione  
 Il `_In_` annotazione indica che:  
  
-   Il parametro deve essere valido e non verrà modificato.  
  
-   La funzione leggerà solo dal buffer a elemento singolo.  
  
-   Il chiamante deve fornire al buffer e inizializzarla.  
  
-   `_In_` Consente di specificare "read-only". Un errore comune consiste nell'applicare `_In_` a un parametro che deve avere il `_Inout_` annotazione invece.  
  
-   `_In_` è consentito ma ignorato dall'analizzatore su valori scalari non puntatore.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Se si usa analisi di Visual Studio Code in questo esempio, verifica che i chiamanti passare un puntatore non Null a un buffer inizializzato per `pInt`. In questo caso, `pInt` puntatore non può essere NULL.  
  
### <a name="example-the-inopt-annotation"></a>Esempio: La \_In_opt\_ annotazione  
 `_In_opt_` equivale a `_In_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve cercare.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio consente di verificare che la funzione controlla i valori NULL prima di accedere ai buffer.  
  
### <a name="example-the-out-annotation"></a>Esempio: La \_Out\_ annotazione  
 `_Out_` supporta uno scenario comune in cui viene passato un puntatore non NULL che punta a un buffer di elemento e la funzione Inizializza l'elemento. Il chiamante non dispone di inizializzare il buffer prima della chiamata. la funzione chiamata promette di inizializzarlo prima della restituzione.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 Visual Studio Code Analysis Tool verifica che il chiamante passa un puntatore non NULL a un buffer per `pInt` e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outopt-annotation"></a>Esempio: La \_Out_opt\_ annotazione  
 `_Out_opt_` equivale a `_Out_`, ad eccezione del fatto che il parametro può essere NULL e, pertanto, la funzione deve cercare.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima `pInt` è dereferenziato e se `pInt` non è NULL, che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-inout-annotation"></a>Esempio: La \_Inout\_ annotazione  
 `_Inout_` viene usato per annotare un parametro del puntatore che può essere modificato dalla funzione. Il puntatore deve puntare a dati inizializzati validi prima della chiamata e anche se subisce delle modifiche, comunque deve avere un valore valido in fase di restituzione. L'annotazione specifica che la funzione può liberamente leggere e scrivere nel buffer di un solo elemento. Il chiamante deve fornire al buffer e inizializzarla.  
  
> [!NOTE]
>  Ad esempio `_Out_`, `_Inout_` necessario applicare a un valore modificabile.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che i chiamanti passare un puntatore non NULL in un buffer inizializzato per `pInt`e che, prima della restituzione, `pInt` ancora non è null e il buffer viene inizializzato.  
  
### <a name="example-the-inoutopt-annotation"></a>Esempio: La \_Inout_opt\_ annotazione  
 `_Inout_opt_` equivale a `_Inout_`, ad eccezione del fatto che il parametro di input può essere NULL e, pertanto, la funzione deve cercare.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima di accedere ai buffer e se `pInt` non è NULL, che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outptr-annotation"></a>Esempio: La \_Outptr\_ annotazione  
 `_Outptr_` viene usato per annotare un parametro che è progettata per restituire un puntatore.  Il parametro stesso non deve essere NULL, la funzione chiamata restituisce un puntatore non NULL e tale puntatore punta a dati inizializzati.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che il chiamante passa un puntatore non NULL `*pInt`, e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-outptropt-annotation"></a>Esempio: La \_Outptr_opt\_ annotazione  
 `_Outptr_opt_` equivale a `_Outptr_`, ad eccezione del fatto che il parametro è facoltativo, il chiamante può passare un puntatore NULL per il parametro.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Analisi del codice di Visual Studio verifica che questa funzione controlla i valori NULL prima `*pInt` è dereferenziato, e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Esempio: La \_Success\_ annotazione in combinazione con \_Out\_  
 Annotazioni possono essere applicate alla maggior parte degli oggetti.  In particolare, è possibile annotare un'intera funzione.  Una delle caratteristiche più ovvie di una funzione è che può avere esito positivo o esito negativo. Ma, come l'associazione tra un buffer e le relative dimensioni, C/C++ non può esprimere funzione esito positivo o negativo. Tramite il `_Success_` annotazione, è possibile dire quali operazioni riuscite per una funzione simile.  Il parametro per il `_Success_` annotazione è semplicemente un'espressione che quando è true indica che la funzione ha avuto esito positivo. L'espressione può essere in grado di gestire il parser di annotazione. Gli effetti delle annotazioni dopo la funzione restituisce sono applicabili solo quando la funzione ha esito positivo. Questo esempio viene illustrato come `_Success_` interagisce con `_Out_` a fare la cosa giusta. È possibile usare la parola chiave `return` per rappresentare il valore restituito.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 Il `_Out_` annotazione fa in modo che analisi di codice di Visual Studio per convalidare che il chiamante passa un puntatore non NULL a un buffer per `pInt`, e che il buffer viene inizializzato dalla funzione prima della restituzione.  
  
## <a name="sal-best-practice"></a>Procedura consigliata SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Aggiunta di annotazioni al codice esistente  
 SAL è una tecnologia potente che può aiutarti a migliorare la sicurezza e affidabilità del codice. Dopo aver imparato SAL, è possibile applicare la nuova competenza per le attività quotidiane. Nel nuovo codice, è possibile usare le specifiche basate su SAL per impostazione predefinita in tutto; nel codice precedente, è possibile aggiungere annotazioni in modo incrementale e pertanto migliorare le prestazioni ogni volta che aggiorna.  
  
 Microsoft pubbliche intestazioni sono già annotate. Pertanto, è consigliabile che nei progetti è prima di tutto annotare le funzioni di nodo foglia e le funzioni che chiamano le API Win32 per ottenere il massimo vantaggio.  
  
### <a name="when-do-i-annotate"></a>Quando annotare?  
 Di seguito sono riportate alcune linee guida:  
  
- Annotare tutti i parametri di puntatore.  
  
- Annotare le annotazioni di intervallo di valori in modo che l'analisi del codice può garantire la sicurezza del buffer e puntatore.  
  
- Annotare le regole di blocco e gli effetti collaterali. Per altre informazioni, vedere [annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md).  
  
- Annotare le proprietà del driver e le altre proprietà specifiche del dominio.  
  
  Oppure è possibile annotare tutti i parametri per rendere il preventivo clear in tutto e rendono più semplice controllare di aver eseguite le annotazioni.  
  
## <a name="related-resources"></a>Risorse correlate  
 [Blog del Team di analisi del codice](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle annotazioni SAL per ridurre i difetti del codice C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotazione di parametri di funzione e valori restituiti](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotazione del comportamento (funzione)](../code-quality/annotating-function-behavior.md)   
 [Annotazioni di struct e classi](../code-quality/annotating-structs-and-classes.md)   
 [Annotazione del comportamento di blocco](../code-quality/annotating-locking-behavior.md)   
 [Specificare quando e dove applicare un'annotazione](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Suggerimenti ed esempi](../code-quality/best-practices-and-examples-sal.md)



