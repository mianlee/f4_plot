# f4_plot


f (pop, Bianbian, L368, Qihe)


```

library(ggplot2) 

# 读入数据和命名每列
Qihe_data <- read.table("Qihe.f4.txt", col.names=c("PopA", "PopB", "PopC", "PopD", "f4", "Z", "std", "SNPs"))

#按照f4的大小排序
Qihe <- Qihe_data[order(Qihe_data$f4),] 

attach(Qihe)

#用ggplot2画图

ggplot(Qihe, aes(y = f4, x = factor(Qihe$PopA, levels = Qihe$PopA))) +    #X以PopA命名
  geom_point(size = 2, colour = "blue", alpha=0.8, shape = 19 ) +         #设置点的大小，颜色，透明度，形状
  theme_bw() +                                                            #背景空白
  coord_flip() +   #X 和 Y 坐标对调
  geom_errorbar(aes(ymin = f4-3*std, ymax = f4+3*std),width = 0, size = 0.2, color = "grey") +  #加入误差线，参数可调，这里是3倍方差
  geom_hline(yintercept = 0, linetype = 2, colour = "grey")+     #加入x零点虚线
  theme(panel.grid.major = element_blank(),                      
        panel.grid.minor = element_blank(),
        axis.line.x = element_line(colour = "black"),
        axis.title = element_blank(),
        axis.text.x = element_text(size =12, margin = margin (t = 9)),
        axis.ticks.length = unit(0.1, "cm"))





#没有注释的code

ggplot(Qihe, aes(y = f4, x = factor(Qihe$PopA, levels = Qihe$PopA))) +
  geom_point(size = 2, colour = "blue", alpha=0.8, shape = 19 ) +
  theme_bw() +
  coord_flip() +
  geom_errorbar(aes(ymin = f4-3*std, ymax = f4+3*std),width = 0, size = 0.2, color = "grey") +
  geom_hline(yintercept = 0, linetype = 2, colour = "grey")+
  theme(panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.line.x = element_line(colour = "black"),
        axis.title = element_blank(),
        axis.text.x = element_text(size =12, margin = margin (t = 9)),
        axis.ticks.length = unit(0.1, "cm"))

```
