# vocalfusion-avs-tests

Tutorial to run XMOS test suite

1) Creating folders

  a) Create your recording folder in ~/Documents/ in the dut_host laptop (can be any name related to the DUT).
  
  b) Create the DUT_audio_tracks folder (called XMOS_Test_Audio) in the home directory of the DUT Host (laptop).
  c) Put the DUT audio tracks in this DUT_audio_tracks folder.
  d) Create the env_audio_tracks folder (called XMOS_Test_Audio) in the Environment Audio Host (laptop) here : /Users/USER_NAME/XMOS_Test_Audio (USER_NAME is the name of the home directory)
  e) Put the environments audio tracks in this env_audio_tracks folder


2) Modify config.json

  a) The 3 speach speakers and the noise Speaker are connected to an External USB audio card. Put its name here (XXXXXXXXX).
  
    "env_audio_host":{
     "env_audio_speakers":"xCORE USB Audio 2.0"
     }

  
  b) Change the label of the Test. It's the first part of the name of every recording. add the ip adress of the DUT host, add the name of the home directory of the dut host ("username"), add the password of the DUT host, if you test VocalFusion, change the dut_reboot_cmd to "~/xmosdfu 0x13 --reboot", if you test Synaptics 2 mics, put nothing (""). Make these changes here :

    "dut_host":{
          "label":"",
          "ip":"",
          "username":"",
          "password":"",
          "wakeword":"beginIndex",
          "dut_reboot_cmd":""
     }

  c) The recordings will be located in the repository "RECORDING_REPO_NAME" (cf 1) a)). Change its name (cf 1) a) (name of this folder)) in the dut_rec_cmd for the three tests (blocks). If you record with Synaptics 2 mic, put 2 instead of 8 channels in the dut_rec_cmd. For each test (block), change USER_NAME of the "env_audio_tracks" with the name of your home directory.

    {
        "dut_play_cmd":"play ",
        "dut_rec_cmd":"rec -b 16 -r 48000 -c 8 ~/Documents/RECORDING_REPO_NAME/",
        "delay_after_dut_audio":"20",
        "env_audio_tracks":[
            "/Users/USER_NAME/XMOS_Test_Audio/Loc1_Noise1_65dB.wav"
          ],
        "dut_audio_tracks":[
            "~/XMOS_Test_Audio/XMOS_DUT1_80dB.wav"
          ],
        "iterations":[1, 2, 3]
    }

3) Run the test
    
  a) On the terminal, go to the folder where wakeword_test.py is located.
  b) Run "python wakeword_test.py config.json" on the terminal
  
4) config.json exemple :

        {
          "env_audio_host":{
              "env_audio_speakers":"xCORE USB Audio 2.0"
          },
          "dut_host":{
              "label":"InHouse_Synaptics_2_mics_20181018",
              "ip":"10.128.29.6",
              "username":"lucianom",
              "password":"password",
              "wakeword":"beginIndex",
              "dut_reboot_cmd":""
          },
          "tests":[
            {
                "dut_play_cmd":"play ",
                "dut_rec_cmd":"rec -b 16 -r 48000 -c 2 ~/Documents/XMOS_Synaptics_2_mics_20181018/",
                "delay_after_dut_audio":"20",
                "env_audio_tracks":[
                    "/Users/xmos/XMOS_Test_Audio/Loc1_Noise1_65dB.wav"
                  ],
                "dut_audio_tracks":[
                    "~/XMOS_Test_Audio/XMOS_DUT1_80dB.wav"
                  ],
               "iterations":[1, 2, 3]
            },
              {
                "dut_play_cmd":"play ",
               "dut_rec_cmd":"rec -b 16 -r 48000 -c 2 ~/Documents/XMOS_Synaptics_2_mics_20181018/",
                "delay_after_dut_audio":"20",
                "env_audio_tracks":[
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Clean.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Clean.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Clean.wav"
                  ],
                "dut_audio_tracks":[
                   "~/XMOS_Test_Audio/XMOS_DUT1_70dB.wav",
                   "~/XMOS_Test_Audio/XMOS_DUT1_80dB.wav",
                   "~/XMOS_Test_Audio/XMOS_DUT1_90dB.wav"
                  ],
               "iterations":[1, 2, 3]
            },
           {
               "dut_play_cmd":"play ",
               "dut_rec_cmd":"rec -b 16 -r 48000 -c 2 ~/Documents/XMOS_Synaptics_2_mics_20181018/",
               "delay_after_dut_audio":"20",
               "env_audio_tracks":[
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Clean.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise1_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise1_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise1_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise1_80dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise2_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise2_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise2_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc1_Noise2_80dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Clean.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise1_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise1_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise1_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise1_80dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise2_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise2_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise2_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc2_Noise2_80dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Clean.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise1_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise1_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise1_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise1_80dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise2_60dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise2_65dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise2_70dB.wav",
                   "/Users/xmos/XMOS_Test_Audio/Loc3_Noise2_80dB.wav"
                 ],
                "dut_audio_tracks":[
                    ""
                  ],
               "iterations":[1, 2, 3]
           }
         ]
        }


