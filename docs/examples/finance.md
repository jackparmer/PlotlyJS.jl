```julia
function ohlc1()
    t = ohlc(open=[33.0, 33.3, 33.5, 33.0, 34.1],
             high=[33.1, 33.3, 33.6, 33.2, 34.8],
             low=[32.7, 32.7, 32.8, 32.6, 32.8],
             close=[33.0, 32.9, 33.3, 33.1, 33.1])
    plot(t)
end
ohlc1()
```


<div id="d6f10877-fc7d-4bc3-97d7-74ec7fc93592" class="plotly-graph-div"></div>

<script>
    window.PLOTLYENV=window.PLOTLYENV || {};
    window.PLOTLYENV.BASE_URL="https://plot.ly";
    Plotly.newPlot('d6f10877-fc7d-4bc3-97d7-74ec7fc93592', [{"high":[33.1,33.3,33.6,33.2,34.8],"type":"ohlc","open":[33.0,33.3,33.5,33.0,34.1],"low":[32.7,32.7,32.8,32.6,32.8],"close":[33.0,32.9,33.3,33.1,33.1]}],
               {"margin":{"l":50,"b":60,"r":50,"t":60}}, {showLink: false});

 </script>



```julia
function ohlc2()
    # uses Quandl.jl

    function get_ohlc(ticker; kwargs...)
        df = quandlget("WIKI/$(ticker)", format="DataFrame")
        ohlc(df, x=:Date, open=:Open, high=:High, low=:Low, close=:Close; kwargs...)
    end

    p1 = plot(get_ohlc("AAPL", name="Apple"), Layout(title="Apple"))
    p2 = plot(get_ohlc("GOOG", name="Google"), Layout(title="Google"))

    [p1 p2]
end
ohlc2()
```


<div id="70e71883-5bff-457f-a3e9-431464686cf1" class="plotly-graph-div"></div>

<script>
    window.PLOTLYENV=window.PLOTLYENV || {};
    window.PLOTLYENV.BASE_URL="https://plot.ly";
    Plotly.newPlot('70e71883-5bff-457f-a3e9-431464686cf1', [{"close":[159.86,161.47,162.91,163.35,164.0,164.05,162.08,161.91,161.26,158.63,161.5,160.82,159.65,158.28,159.88,158.67,158.73,156.07,153.39,151.89,150.55,153.14,154.23,153.28,154.12,153.81,154.48,153.4508,155.39,155.3,155.84,155.9,156.55,156.0,156.99,159.88,160.47,159.76,155.98,156.16,156.17,157.1,156.405,157.41,163.05,166.72,169.04,166.89,168.11,172.5,174.25,174.81,175.88,174.67,173.97,171.34,169.08,171.1,170.15,169.98,173.14,174.96,174.97,174.09,173.07,169.48,171.85,171.05,169.8,169.64,169.01,169.452,169.37,172.67,171.7,172.27,172.22,173.87,176.42,174.54,174.35,175.01,175.01,170.57,170.6,171.08,169.23,172.26,172.23,173.03,175.0,174.35,174.33,174.29,175.28,177.09,176.19,179.1,179.26,178.46],"xaxis":"x1","high":[160.56,162.0,163.12,163.89,164.52,164.94,164.25,162.99,162.24,161.15,162.05,163.96,159.96,159.4,160.97,160.5,159.77,158.26,155.8,152.27,151.83,153.92,154.7189,154.28,154.13,154.45,155.09,153.86,155.44,155.49,156.73,158.0,156.98,157.37,157.28,160.0,160.87,160.71,157.08,157.75,157.69,157.42,157.55,157.8295,163.6,168.07,169.6499,169.94,168.5,174.26,174.99,175.25,176.095,175.38,174.5,173.48,170.3197,171.87,171.39,170.56,173.7,175.0,175.5,175.08,174.87,172.92,172.14,171.67,172.62,171.52,170.2047,170.44,171.0,172.89,172.39,173.54,173.13,174.17,177.2,175.39,175.42,176.02,175.424,171.47,170.78,171.85,170.59,172.3,174.55,173.47,175.37,175.61,175.06,174.3,175.4886,177.36,179.39,179.25,180.1,179.58],"type":"ohlc","name":"Apple","open":[159.65,160.14,160.1,163.8,163.64,164.8,163.75,162.71,162.09,160.86,160.5,162.61,159.87,158.99,158.47,160.11,159.51,157.9,155.8,152.02,149.99,151.78,153.8,153.89,153.21,154.26,154.01,153.63,154.18,154.97,155.81,156.055,155.97,156.35,156.73,157.9,159.78,160.42,156.75,156.61,156.89,156.29,156.91,157.23,159.29,163.89,167.9,169.87,167.64,174.0,172.365,173.91,175.11,175.11,173.5,173.04,169.97,171.18,171.04,170.29,170.78,173.36,175.1,175.05,174.3,172.63,170.43,169.95,172.48,169.06,167.5,169.03,170.49,169.2,172.15,172.5,172.4,173.63,174.88,175.03,174.87,174.17,174.68,170.8,170.1,171.0,170.52,170.16,172.53,172.54,173.44,174.35,174.55,173.16,174.59,176.18,177.9,176.15,179.37,178.61],"low":[159.27,159.93,160.0,162.61,163.48,163.63,160.56,160.52,160.36,158.53,159.89,158.77,157.91,158.09,158.0,157.995,158.44,153.83,152.75,150.56,149.16,151.69,153.54,152.7,152.0,152.72,153.91,152.46,154.05,154.56,155.485,155.1,155.75,155.7299,156.41,157.65,159.23,159.6,155.02,155.96,155.5,156.2,155.27,156.78,158.7,163.72,166.94,165.61,165.28,171.12,171.72,173.6,173.14,174.27,173.4,171.18,168.38,170.3,169.64,169.56,170.78,173.05,174.6459,173.34,171.86,167.16,168.44,168.5,169.63,168.4,166.46,168.91,168.82,168.79,171.461,172.0,171.65,172.46,174.86,174.09,173.25,174.1,174.5,169.679,169.71,170.48,169.22,169.26,171.96,172.08,173.05,173.93,173.41,173.0,174.49,175.65,176.14,175.07,178.25,177.41],"yaxis":"y1","x":["2017-08-25","2017-08-28","2017-08-29","2017-08-30","2017-08-31","2017-09-01","2017-09-05","2017-09-06","2017-09-07","2017-09-08","2017-09-11","2017-09-12","2017-09-13","2017-09-14","2017-09-15","2017-09-18","2017-09-19","2017-09-20","2017-09-21","2017-09-22","2017-09-25","2017-09-26","2017-09-27","2017-09-28","2017-09-29","2017-10-02","2017-10-03","2017-10-04","2017-10-05","2017-10-06","2017-10-09","2017-10-10","2017-10-11","2017-10-12","2017-10-13","2017-10-16","2017-10-17","2017-10-18","2017-10-19","2017-10-20","2017-10-23","2017-10-24","2017-10-25","2017-10-26","2017-10-27","2017-10-30","2017-10-31","2017-11-01","2017-11-02","2017-11-03","2017-11-06","2017-11-07","2017-11-09","2017-11-10","2017-11-13","2017-11-14","2017-11-15","2017-11-16","2017-11-17","2017-11-20","2017-11-21","2017-11-22","2017-11-24","2017-11-27","2017-11-28","2017-11-29","2017-11-30","2017-12-01","2017-12-04","2017-12-05","2017-12-06","2017-12-07","2017-12-08","2017-12-11","2017-12-12","2017-12-13","2017-12-14","2017-12-15","2017-12-18","2017-12-19","2017-12-20","2017-12-21","2017-12-22","2017-12-26","2017-12-27","2017-12-28","2017-12-29","2018-01-02","2018-01-03","2018-01-04","2018-01-05","2018-01-08","2018-01-09","2018-01-10","2018-01-11","2018-01-12","2018-01-16","2018-01-17","2018-01-18","2018-01-19"]},{"close":[915.89,913.81,921.29,929.57,939.33,937.34,928.45,927.81,935.95,926.5,929.08,932.07,935.09,925.11,920.29,915.0,921.81,931.58,932.45,928.53,920.97,924.86,944.49,949.5,959.11,953.27,957.79,951.68,969.96,978.89,977.0,972.6,989.25,987.83,989.68,992.0,992.18,992.81,984.45,988.2,968.45,970.54,973.33,972.56,1019.27,1017.11,1016.64,1025.5,1025.58,1032.48,1025.9,1033.33,1031.26,1028.07,1025.75,1026.0,1020.91,1032.5,1019.09,1018.38,1034.49,1035.96,1040.61,1054.21,1047.41,1021.66,1021.41,1010.17,998.68,1005.15,1018.38,1030.93,1037.05,1041.1,1040.48,1040.61,1049.15,1064.19,1077.14,1070.68,1064.95,1063.63,1060.12,1056.74,1049.37,1048.14,1046.4,1065.0,1082.48,1086.4,1102.23,1106.94,1106.26,1102.61,1105.52,1122.26,1121.76,1131.98,1129.79,1137.51],"xaxis":"x2","high":[925.555,919.245,923.33,930.819,941.98,942.48,937.0,930.915,936.41,936.99,938.38,933.48,937.25,932.77,926.49,922.08,922.4199,933.88,936.53,934.73,926.4,930.82,949.9,950.69,959.7864,962.54,958.0,960.39,970.91,979.46,985.425,981.57,990.71,994.12,997.21,993.9065,996.44,996.72,988.88,991.0,989.52,972.23,976.09,987.6,1048.39,1024.97,1024.0,1029.67,1028.09,1032.65,1034.87,1033.97,1033.99,1030.76,1031.58,1026.81,1024.09,1035.92,1034.42,1022.61,1035.11,1039.71,1043.18,1055.46,1062.38,1044.08,1028.49,1022.49,1016.1,1020.61,1024.97,1034.24,1042.05,1043.8,1050.31,1046.66,1058.5,1067.62,1078.49,1076.84,1073.38,1069.33,1064.2,1060.12,1058.37,1054.75,1049.7,1066.94,1086.29,1093.57,1104.25,1111.27,1110.57,1104.6,1106.53,1124.29,1139.91,1132.6,1132.51,1137.86],"type":"ohlc","name":"Google","open":[923.49,916.0,905.1,920.05,931.76,941.13,933.08,930.15,931.73,936.49,934.25,932.59,930.66,931.25,924.66,920.01,917.42,922.98,933.0,927.75,925.45,923.72,927.74,941.36,952.0,959.98,954.0,957.0,955.49,966.7,980.0,980.0,973.72,987.45,992.0,992.1,990.29,991.77,986.0,989.44,989.52,970.0,968.37,980.0,1009.19,1014.0,1015.22,1017.21,1021.76,1022.11,1028.99,1027.27,1033.99,1026.46,1023.42,1022.59,1019.21,1022.52,1034.01,1020.26,1023.31,1035.0,1035.87,1040.0,1055.09,1042.68,1022.37,1015.8,1012.66,995.94,1001.5,1020.43,1037.49,1035.5,1039.63,1046.12,1045.0,1054.61,1066.08,1075.2,1071.78,1064.95,1061.11,1058.07,1057.39,1051.6,1046.72,1048.34,1064.31,1088.0,1094.0,1102.23,1109.4,1097.1,1106.3,1102.41,1132.51,1126.22,1131.41,1131.83],"low":[915.5,911.87,905.0,919.65,931.76,935.15,921.96,919.27,923.62,924.88,926.92,923.861,929.86,924.0,916.36,910.6,912.55,922.0,923.83,926.48,909.7,921.14,927.74,940.55,951.51,947.84,949.14,950.69,955.18,963.36,976.11,966.0801,972.25,985.0,989.0,984.0,988.59,986.9747,978.39,984.58,966.12,961.0,960.5201,972.2,1008.2,1007.5,1010.42,1016.95,1013.01,1020.31,1025.0,1025.13,1019.67,1025.28,1022.57,1014.15,1015.42,1022.52,1017.75,1017.5,1022.66,1031.43,1035.0,1038.44,1040.0,1015.65,1015.0,1002.02,995.57,988.28,1001.14,1018.07,1032.52,1032.05,1033.69,1038.38,1043.11,1049.5,1062.0,1063.55,1061.52,1061.79,1059.44,1050.2,1048.05,1044.77,1044.9,1045.23,1063.21,1084.0,1092.0,1101.62,1101.23,1096.11,1099.59,1101.15,1117.83,1117.01,1117.5,1128.3],"yaxis":"y2","x":["2017-08-25","2017-08-28","2017-08-29","2017-08-30","2017-08-31","2017-09-01","2017-09-05","2017-09-06","2017-09-07","2017-09-08","2017-09-11","2017-09-12","2017-09-13","2017-09-14","2017-09-15","2017-09-18","2017-09-19","2017-09-20","2017-09-21","2017-09-22","2017-09-25","2017-09-26","2017-09-27","2017-09-28","2017-09-29","2017-10-02","2017-10-03","2017-10-04","2017-10-05","2017-10-06","2017-10-09","2017-10-10","2017-10-11","2017-10-12","2017-10-13","2017-10-16","2017-10-17","2017-10-18","2017-10-19","2017-10-20","2017-10-23","2017-10-24","2017-10-25","2017-10-26","2017-10-27","2017-10-30","2017-10-31","2017-11-01","2017-11-02","2017-11-03","2017-11-06","2017-11-07","2017-11-09","2017-11-10","2017-11-13","2017-11-14","2017-11-15","2017-11-16","2017-11-17","2017-11-20","2017-11-21","2017-11-22","2017-11-24","2017-11-27","2017-11-28","2017-11-29","2017-11-30","2017-12-01","2017-12-04","2017-12-05","2017-12-06","2017-12-07","2017-12-08","2017-12-11","2017-12-12","2017-12-13","2017-12-14","2017-12-15","2017-12-18","2017-12-19","2017-12-20","2017-12-21","2017-12-22","2017-12-26","2017-12-27","2017-12-28","2017-12-29","2018-01-02","2018-01-03","2018-01-04","2018-01-05","2018-01-08","2018-01-09","2018-01-10","2018-01-11","2018-01-12","2018-01-16","2018-01-17","2018-01-18","2018-01-19"]}],
               {"xaxis1":{"domain":[0.0,0.45],"anchor":"y1"},"yaxis1":{"domain":[0.0,1.0],"anchor":"x1"},"xaxis2":{"domain":[0.55,1.0],"anchor":"y2"},"annotations":[{"yanchor":"bottom","xanchor":"center","y":1.0,"font":{"size":16},"showarrow":false,"yref":"paper","text":"Apple","xref":"paper","x":0.225},{"yanchor":"bottom","xanchor":"center","y":1.0,"font":{"size":16},"showarrow":false,"yref":"paper","text":"Google","xref":"paper","x":0.775}],"margin":{"l":50,"b":60,"r":50,"t":60},"yaxis2":{"domain":[0.0,1.0],"anchor":"x2"}}, {showLink: false});

 </script>



```julia
function candlestick1()
    t = candlestick(open=[33.0, 33.3, 33.5, 33.0, 34.1],
                    high=[33.1, 33.3, 33.6, 33.2, 34.8],
                    low=[32.7, 32.7, 32.8, 32.6, 32.8],
                    close=[33.0, 32.9, 33.3, 33.1, 33.1])
    plot(t)
end
candlestick1()
```


<div id="a1fff4fe-7068-499a-9ed6-5fe4402c72e8" class="plotly-graph-div"></div>

<script>
    window.PLOTLYENV=window.PLOTLYENV || {};
    window.PLOTLYENV.BASE_URL="https://plot.ly";
    Plotly.newPlot('a1fff4fe-7068-499a-9ed6-5fe4402c72e8', [{"high":[33.1,33.3,33.6,33.2,34.8],"type":"candlestick","open":[33.0,33.3,33.5,33.0,34.1],"low":[32.7,32.7,32.8,32.6,32.8],"close":[33.0,32.9,33.3,33.1,33.1]}],
               {"margin":{"l":50,"b":60,"r":50,"t":60}}, {showLink: false});

 </script>



```julia
function candlestick2()
    # uses Quandl.jl

    function get_candlestick(ticker; kwargs...)
        df = quandlget("WIKI/$(ticker)", format="DataFrame")
        candlestick(df, x=:Date, open=:Open, high=:High, low=:Low, close=:Close; kwargs...)
    end

    p1 = plot(get_candlestick("AAPL", name="Apple"), Layout(title="Apple"))
    p2 = plot(get_candlestick("GOOG", name="Google"), Layout(title="Google"))

    [p1 p2]
end
candlestick2()
```


<div id="360a4830-46fc-4469-bdb9-79c8226db9a8" class="plotly-graph-div"></div>

<script>
    window.PLOTLYENV=window.PLOTLYENV || {};
    window.PLOTLYENV.BASE_URL="https://plot.ly";
    Plotly.newPlot('360a4830-46fc-4469-bdb9-79c8226db9a8', [{"close":[159.86,161.47,162.91,163.35,164.0,164.05,162.08,161.91,161.26,158.63,161.5,160.82,159.65,158.28,159.88,158.67,158.73,156.07,153.39,151.89,150.55,153.14,154.23,153.28,154.12,153.81,154.48,153.4508,155.39,155.3,155.84,155.9,156.55,156.0,156.99,159.88,160.47,159.76,155.98,156.16,156.17,157.1,156.405,157.41,163.05,166.72,169.04,166.89,168.11,172.5,174.25,174.81,175.88,174.67,173.97,171.34,169.08,171.1,170.15,169.98,173.14,174.96,174.97,174.09,173.07,169.48,171.85,171.05,169.8,169.64,169.01,169.452,169.37,172.67,171.7,172.27,172.22,173.87,176.42,174.54,174.35,175.01,175.01,170.57,170.6,171.08,169.23,172.26,172.23,173.03,175.0,174.35,174.33,174.29,175.28,177.09,176.19,179.1,179.26,178.46],"xaxis":"x1","high":[160.56,162.0,163.12,163.89,164.52,164.94,164.25,162.99,162.24,161.15,162.05,163.96,159.96,159.4,160.97,160.5,159.77,158.26,155.8,152.27,151.83,153.92,154.7189,154.28,154.13,154.45,155.09,153.86,155.44,155.49,156.73,158.0,156.98,157.37,157.28,160.0,160.87,160.71,157.08,157.75,157.69,157.42,157.55,157.8295,163.6,168.07,169.6499,169.94,168.5,174.26,174.99,175.25,176.095,175.38,174.5,173.48,170.3197,171.87,171.39,170.56,173.7,175.0,175.5,175.08,174.87,172.92,172.14,171.67,172.62,171.52,170.2047,170.44,171.0,172.89,172.39,173.54,173.13,174.17,177.2,175.39,175.42,176.02,175.424,171.47,170.78,171.85,170.59,172.3,174.55,173.47,175.37,175.61,175.06,174.3,175.4886,177.36,179.39,179.25,180.1,179.58],"type":"candlestick","name":"Apple","open":[159.65,160.14,160.1,163.8,163.64,164.8,163.75,162.71,162.09,160.86,160.5,162.61,159.87,158.99,158.47,160.11,159.51,157.9,155.8,152.02,149.99,151.78,153.8,153.89,153.21,154.26,154.01,153.63,154.18,154.97,155.81,156.055,155.97,156.35,156.73,157.9,159.78,160.42,156.75,156.61,156.89,156.29,156.91,157.23,159.29,163.89,167.9,169.87,167.64,174.0,172.365,173.91,175.11,175.11,173.5,173.04,169.97,171.18,171.04,170.29,170.78,173.36,175.1,175.05,174.3,172.63,170.43,169.95,172.48,169.06,167.5,169.03,170.49,169.2,172.15,172.5,172.4,173.63,174.88,175.03,174.87,174.17,174.68,170.8,170.1,171.0,170.52,170.16,172.53,172.54,173.44,174.35,174.55,173.16,174.59,176.18,177.9,176.15,179.37,178.61],"low":[159.27,159.93,160.0,162.61,163.48,163.63,160.56,160.52,160.36,158.53,159.89,158.77,157.91,158.09,158.0,157.995,158.44,153.83,152.75,150.56,149.16,151.69,153.54,152.7,152.0,152.72,153.91,152.46,154.05,154.56,155.485,155.1,155.75,155.7299,156.41,157.65,159.23,159.6,155.02,155.96,155.5,156.2,155.27,156.78,158.7,163.72,166.94,165.61,165.28,171.12,171.72,173.6,173.14,174.27,173.4,171.18,168.38,170.3,169.64,169.56,170.78,173.05,174.6459,173.34,171.86,167.16,168.44,168.5,169.63,168.4,166.46,168.91,168.82,168.79,171.461,172.0,171.65,172.46,174.86,174.09,173.25,174.1,174.5,169.679,169.71,170.48,169.22,169.26,171.96,172.08,173.05,173.93,173.41,173.0,174.49,175.65,176.14,175.07,178.25,177.41],"yaxis":"y1","x":["2017-08-25","2017-08-28","2017-08-29","2017-08-30","2017-08-31","2017-09-01","2017-09-05","2017-09-06","2017-09-07","2017-09-08","2017-09-11","2017-09-12","2017-09-13","2017-09-14","2017-09-15","2017-09-18","2017-09-19","2017-09-20","2017-09-21","2017-09-22","2017-09-25","2017-09-26","2017-09-27","2017-09-28","2017-09-29","2017-10-02","2017-10-03","2017-10-04","2017-10-05","2017-10-06","2017-10-09","2017-10-10","2017-10-11","2017-10-12","2017-10-13","2017-10-16","2017-10-17","2017-10-18","2017-10-19","2017-10-20","2017-10-23","2017-10-24","2017-10-25","2017-10-26","2017-10-27","2017-10-30","2017-10-31","2017-11-01","2017-11-02","2017-11-03","2017-11-06","2017-11-07","2017-11-09","2017-11-10","2017-11-13","2017-11-14","2017-11-15","2017-11-16","2017-11-17","2017-11-20","2017-11-21","2017-11-22","2017-11-24","2017-11-27","2017-11-28","2017-11-29","2017-11-30","2017-12-01","2017-12-04","2017-12-05","2017-12-06","2017-12-07","2017-12-08","2017-12-11","2017-12-12","2017-12-13","2017-12-14","2017-12-15","2017-12-18","2017-12-19","2017-12-20","2017-12-21","2017-12-22","2017-12-26","2017-12-27","2017-12-28","2017-12-29","2018-01-02","2018-01-03","2018-01-04","2018-01-05","2018-01-08","2018-01-09","2018-01-10","2018-01-11","2018-01-12","2018-01-16","2018-01-17","2018-01-18","2018-01-19"]},{"close":[915.89,913.81,921.29,929.57,939.33,937.34,928.45,927.81,935.95,926.5,929.08,932.07,935.09,925.11,920.29,915.0,921.81,931.58,932.45,928.53,920.97,924.86,944.49,949.5,959.11,953.27,957.79,951.68,969.96,978.89,977.0,972.6,989.25,987.83,989.68,992.0,992.18,992.81,984.45,988.2,968.45,970.54,973.33,972.56,1019.27,1017.11,1016.64,1025.5,1025.58,1032.48,1025.9,1033.33,1031.26,1028.07,1025.75,1026.0,1020.91,1032.5,1019.09,1018.38,1034.49,1035.96,1040.61,1054.21,1047.41,1021.66,1021.41,1010.17,998.68,1005.15,1018.38,1030.93,1037.05,1041.1,1040.48,1040.61,1049.15,1064.19,1077.14,1070.68,1064.95,1063.63,1060.12,1056.74,1049.37,1048.14,1046.4,1065.0,1082.48,1086.4,1102.23,1106.94,1106.26,1102.61,1105.52,1122.26,1121.76,1131.98,1129.79,1137.51],"xaxis":"x2","high":[925.555,919.245,923.33,930.819,941.98,942.48,937.0,930.915,936.41,936.99,938.38,933.48,937.25,932.77,926.49,922.08,922.4199,933.88,936.53,934.73,926.4,930.82,949.9,950.69,959.7864,962.54,958.0,960.39,970.91,979.46,985.425,981.57,990.71,994.12,997.21,993.9065,996.44,996.72,988.88,991.0,989.52,972.23,976.09,987.6,1048.39,1024.97,1024.0,1029.67,1028.09,1032.65,1034.87,1033.97,1033.99,1030.76,1031.58,1026.81,1024.09,1035.92,1034.42,1022.61,1035.11,1039.71,1043.18,1055.46,1062.38,1044.08,1028.49,1022.49,1016.1,1020.61,1024.97,1034.24,1042.05,1043.8,1050.31,1046.66,1058.5,1067.62,1078.49,1076.84,1073.38,1069.33,1064.2,1060.12,1058.37,1054.75,1049.7,1066.94,1086.29,1093.57,1104.25,1111.27,1110.57,1104.6,1106.53,1124.29,1139.91,1132.6,1132.51,1137.86],"type":"candlestick","name":"Google","open":[923.49,916.0,905.1,920.05,931.76,941.13,933.08,930.15,931.73,936.49,934.25,932.59,930.66,931.25,924.66,920.01,917.42,922.98,933.0,927.75,925.45,923.72,927.74,941.36,952.0,959.98,954.0,957.0,955.49,966.7,980.0,980.0,973.72,987.45,992.0,992.1,990.29,991.77,986.0,989.44,989.52,970.0,968.37,980.0,1009.19,1014.0,1015.22,1017.21,1021.76,1022.11,1028.99,1027.27,1033.99,1026.46,1023.42,1022.59,1019.21,1022.52,1034.01,1020.26,1023.31,1035.0,1035.87,1040.0,1055.09,1042.68,1022.37,1015.8,1012.66,995.94,1001.5,1020.43,1037.49,1035.5,1039.63,1046.12,1045.0,1054.61,1066.08,1075.2,1071.78,1064.95,1061.11,1058.07,1057.39,1051.6,1046.72,1048.34,1064.31,1088.0,1094.0,1102.23,1109.4,1097.1,1106.3,1102.41,1132.51,1126.22,1131.41,1131.83],"low":[915.5,911.87,905.0,919.65,931.76,935.15,921.96,919.27,923.62,924.88,926.92,923.861,929.86,924.0,916.36,910.6,912.55,922.0,923.83,926.48,909.7,921.14,927.74,940.55,951.51,947.84,949.14,950.69,955.18,963.36,976.11,966.0801,972.25,985.0,989.0,984.0,988.59,986.9747,978.39,984.58,966.12,961.0,960.5201,972.2,1008.2,1007.5,1010.42,1016.95,1013.01,1020.31,1025.0,1025.13,1019.67,1025.28,1022.57,1014.15,1015.42,1022.52,1017.75,1017.5,1022.66,1031.43,1035.0,1038.44,1040.0,1015.65,1015.0,1002.02,995.57,988.28,1001.14,1018.07,1032.52,1032.05,1033.69,1038.38,1043.11,1049.5,1062.0,1063.55,1061.52,1061.79,1059.44,1050.2,1048.05,1044.77,1044.9,1045.23,1063.21,1084.0,1092.0,1101.62,1101.23,1096.11,1099.59,1101.15,1117.83,1117.01,1117.5,1128.3],"yaxis":"y2","x":["2017-08-25","2017-08-28","2017-08-29","2017-08-30","2017-08-31","2017-09-01","2017-09-05","2017-09-06","2017-09-07","2017-09-08","2017-09-11","2017-09-12","2017-09-13","2017-09-14","2017-09-15","2017-09-18","2017-09-19","2017-09-20","2017-09-21","2017-09-22","2017-09-25","2017-09-26","2017-09-27","2017-09-28","2017-09-29","2017-10-02","2017-10-03","2017-10-04","2017-10-05","2017-10-06","2017-10-09","2017-10-10","2017-10-11","2017-10-12","2017-10-13","2017-10-16","2017-10-17","2017-10-18","2017-10-19","2017-10-20","2017-10-23","2017-10-24","2017-10-25","2017-10-26","2017-10-27","2017-10-30","2017-10-31","2017-11-01","2017-11-02","2017-11-03","2017-11-06","2017-11-07","2017-11-09","2017-11-10","2017-11-13","2017-11-14","2017-11-15","2017-11-16","2017-11-17","2017-11-20","2017-11-21","2017-11-22","2017-11-24","2017-11-27","2017-11-28","2017-11-29","2017-11-30","2017-12-01","2017-12-04","2017-12-05","2017-12-06","2017-12-07","2017-12-08","2017-12-11","2017-12-12","2017-12-13","2017-12-14","2017-12-15","2017-12-18","2017-12-19","2017-12-20","2017-12-21","2017-12-22","2017-12-26","2017-12-27","2017-12-28","2017-12-29","2018-01-02","2018-01-03","2018-01-04","2018-01-05","2018-01-08","2018-01-09","2018-01-10","2018-01-11","2018-01-12","2018-01-16","2018-01-17","2018-01-18","2018-01-19"]}],
               {"xaxis1":{"domain":[0.0,0.45],"anchor":"y1"},"yaxis1":{"domain":[0.0,1.0],"anchor":"x1"},"xaxis2":{"domain":[0.55,1.0],"anchor":"y2"},"annotations":[{"yanchor":"bottom","xanchor":"center","y":1.0,"font":{"size":16},"showarrow":false,"yref":"paper","text":"Apple","xref":"paper","x":0.225},{"yanchor":"bottom","xanchor":"center","y":1.0,"font":{"size":16},"showarrow":false,"yref":"paper","text":"Google","xref":"paper","x":0.775}],"margin":{"l":50,"b":60,"r":50,"t":60},"yaxis2":{"domain":[0.0,1.0],"anchor":"x2"}}, {showLink: false});

 </script>


