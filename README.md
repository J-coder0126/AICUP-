# AICUP 使用手冊  
以上14個文件檔案以及1個環境安裝檔案都需要用到
****
## 創建環境
創建任務一 whisperX-large v3環境
    
    conda create -n <your_env_name> -f environment_whisperx.yml

****
## 任務一 錄音檔案轉為文字稿  
使用以下程式碼，將錄音檔轉為文字稿
*需修改 `AI_CUP_whisper_output_dictionary` 檔案內 `audio_dir` 更換為所需的錄音檔案
    

    python AI_CUP_whisper_output_dictionary.py

使用以下程式碼，將文字稿整合成上傳txt檔案  
*需修改 `task1flie_task1ans` 檔案內 `path` 更換為文字稿
    
    python task1flie_task1ans.py

****
## 任務二 找出敏感字詞
由於本組中文英文分開處理，故首先將txt以及json檔案的中文與英文分開    
*需修改 `split_ch_en`、`split_json_ch_en` 檔案內 `folder_path` 資料夾路徑  
txt檔案使用
    
    python split_ch_en.py

json檔案使用  

    python split_json_ch_en.py

## 接下來先處理中文檔案  
使用以下程式碼，對中文文字稿做推論    
*需修改 `AI_CUP_API_connect_set_test` 檔案內 `INPUT_FOLDER` 、 `OUTPUT_PATH` 資料夾路徑以及輸出txt檔案路徑
    
    python AI_CUP_API_connect_set_test.py
使用以下程式碼，清理推論結果中不需要的文字  
*需修改`AI_CUP_clean_predictions`檔案內 `input_path`、`output_path` txt檔案的輸入及輸出路徑  

    python AI_CUP_clean_predictions.py
使用以下程式碼，找出敏感字詞中的特殊字元  
******************這邊還沒打完
    
    python chinese_find_symbol.py
使用以下程式碼，將文字稿的敏感字詞對回去json檔中的時間以抓出敏感字詞的時間序  
*需修改`chinese_timestep` 檔案內`local`  local需包含中文的txt以及json資料夾  
    
    python chinese_timestep.py 



    


    
