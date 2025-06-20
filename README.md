# AICUP 使用手冊  
以上14個文件檔案以及2個環境安裝檔案都需要用到
****
## 創建環境
創建任務一 whisperX-large v3環境
    
    conda create -n <your_env_name1> -f environment_whisperx.yml
創建任務二 推論環境  

    conda create -n <your_env_name2> -f task2_env.yml
****
## 任務一 錄音檔案轉為文字稿 
使用以下程式碼，啟動環境

    conda acitvate <your_env_name1>
    
使用以下程式碼，將錄音檔轉為文字稿  
*需修改 `AI_CUP_whisper_output_dictionary` 檔案內 `audio_dir` 更換為所需的錄音檔案
    
    python AI_CUP_whisper_output_dictionary.py

使用以下程式碼，將文字稿整合成上傳txt檔案  
*需修改 `task1flie_task1ans` 檔案內 `path` 更換為文字稿
    
    python task1flie_task1ans.py

****
## 任務二 找出敏感字詞
使用以下程式碼，啟動環境  

    conda acitvate <your_env_name2>
由於本組中文英文分開處理，故首先將txt以及json檔案的中文與英文分開    
*需修改 `split_ch_en`、`split_json_ch_en` 檔案內 `folder_path` 資料夾路徑  
txt檔案使用
    
    python split_ch_en.py

json檔案使用  

    python split_json_ch_en.py

## 處理中文檔案  
使用以下程式碼，對中文文字稿做推論    
*需修改 `AI_CUP_API_connect_set_test` 檔案內 `INPUT_FOLDER` 、 `OUTPUT_PATH` 資料夾路徑以及輸出txt檔案路徑
    
    python AI_CUP_API_connect_set_test.py
使用以下程式碼，清理推論結果中不需要的文字  
*需修改`AI_CUP_clean_predictions`檔案內 `input_path`、`output_path` txt檔案的輸入及輸出路徑  

    python AI_CUP_clean_predictions.py
使用以下程式碼，找出敏感字詞中的特殊字元  
*需修改`chinese_find_symbol` 檔案內 `local` 分割後的中文txt檔案
    
    python chinese_find_symbol.py
使用以下程式碼，將文字稿的敏感字詞對回去json檔中的時間以抓出敏感字詞的時間序  
*需修改`chinese_timestep` 檔案內`local`  local需包含中文的txt以及json資料夾  
*第252、260行需設定輸出資料夾分別為有對到時間序的檔案及沒對到時間序的檔案
    
    python chinese_timestep.py 

輸出結果及為任務二中文的敏感字詞結果
## 處理英文檔案
使用以下程式碼，對英文文字稿做推論  
*需修改`rag` 檔案內 `os.environ`、`txt_path`設定GPU以及英文txt資料夾路徑    

    python rag.py
使用以下程式碼，清理推論結果中不需要的文字  
*需修改`clean_data`檔案內的第14行、第168行，設定推論文字檔及輸出檔案\
        
    python clean_data.py
使用以下程式碼，找出敏感字詞中的特殊字元      
*需修改`English_find_symbol` 檔案內 `local` 分割後的英文txt檔案 
        
    python English_find_symbol.py

使用以下程式碼，將文字稿的敏感字詞對回去json檔中的時間以抓出敏感字詞的時間序  
*需修改`English_timestep` 檔案內`local`  local需包含中文的txt以及json資料夾  
*第252、260行需設定輸出資料夾分別為有對到時間序的檔案及沒對到時間序的檔案
        
    python English_timestep.py

使用以下程式碼，將英文檔案中沒有對到的檔案進行模糊查詢再匹配一次  
*需修改 `fuzzy` 檔案內 `p_txt`、`output_txt`、`json_folder`，分別代表英文沒對到的檔案、輸出路徑英文json檔案  

    python fuzzy.py
    
## 合併中英文結果
使用以下程式碼，將中文英文檔案合併成最終結果  
*需修改`concate`檔案內第20行，分別代表英文結果、中文結果、輸出txt檔案  

    python concate.py

    
