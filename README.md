
# Set Up

```
cols = 
```

# Specific Charts

## Bar Chart

### Column Chart

```
chart_name_col <- dataset %>%
  ggplot(aes(x = x_axis_variable, y = y_axis_variable, fill = x_axis_variable)) +
  geom_col() +
  scale_fill_manual(values = cols, name = "name_of_legend") +
  theme_minimal() +
  theme(legend.position = "none", # hides legend 
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        text = element_text(family = "Palatino")) +
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```
<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  chart_name_bw <- dataset %>%
  ggplot(aes(x = x_axis_variable, y = Count, fill = Policy)) + # use x = reorder(...) if needed
  geom_col() +
  scale_fill_manual(values = b_w, name = "name_of_legend") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.line.x = element_line(colour = "black", linewidth = 0.2),
        axis.line.y = element_line(colour = "black", linewidth = 0.2),
        text = element_text(family = "Palatino")) +
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
    ```

</details>

### Stacked Bar Chart

```
chart_name_col <- data_set %>%
  ggplot(aes(y=y_axis_variable, fill= stacked_variable, x = x_axis_variable)) +
  geom_bar(position = "stack", stat="identity", width = 0.55,
  color = "black",
  linewidth = 0.25) +
  scale_fill_manual(name = "", values = cols) +
   geom_text_repel(data = subset(dataset, percent > 0),
                   aes(y = midpoint, label = paste0(percent, "%")),
            nudge_x = 0.45,
            segment.size = 0.3,
            segment.color = "black",
            show.legend = FALSE,
            family = "Palatino",
            force = 1.1,
            size = 3,
            color = "black",
            point.padding = unit(3.5, "lines"))  +
  theme_minimal()+
  labs(title = "title of chart, only capitalize first word",
       y = "Percent",
       x = "") +
  ylim(0, 110) +
  theme(text = element_text(family = "Palatino", size = 12),
        axis.title.y = element_text(margin = margin(r = 10)))
```
<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  chart_name_bw <- data_set %>%
  ggplot(aes(y=y_axis_variable, fill= stacked_variable, x = x_axis_variable)) +
  geom_bar(position = "stack", stat="identity", width = 0.55,
  color = "black",
  linewidth = 0.25) +
  scale_fill_manual(name = "", values = b_w) +
   geom_text_repel(data = subset(dataset, percent > 0),
                   aes(y = midpoint, label = paste0(percent, "%")),
            nudge_x = 0.45,
            segment.size = 0.3,
            segment.color = "black",
            show.legend = FALSE,
            family = "Palatino",
            force = 1.1,
            size = 3,
            color = "black",
            point.padding = unit(3.5, "lines"))  +
  theme_minimal()+
  labs(title = "title of chart, only capitalize first word",
       y = "Percent",
       x = "") +
  ylim(0, 110) +
  theme(text = element_text(family = "Palatino", size = 12),
        axis.title.y = element_text(margin = margin(r = 10))) +
  theme(panel.grid.major = element_blank(),
        panel.grid.minor = element_blank())
    ```

</details>

### Horizontal Bart Chart


### Clustered Bar Chart

```
chart_name_col <- dataset %>%
ggplot(aes(x = x_axis_variable, y = y_axis_variable, fill = clustered_variable)) + # in example clustered_variables are ACT and SAT
  geom_bar(position = "dodge", stat = "identity") +
  scale_fill_manual(values = c("#color_code", "#color_code"), labels = c("clustered_value1", "clustered_value2")) +  # to manual label clustered values
  labs(x =  "x_axis_title", y = "y_axis_title", fill = "clustered_variable", title = "title of chart, only capitalize first word") +
  scale_y_continuous(breaks = c(0.2, 0.4, 0.6), 
                    labels = c("20%", "40%", "60%")) + # decide how to scale y axis
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1),
        text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        plot.title = element_text(size = 16)) 
```

<details>
  <summary><b>Black and white version</b></summary>
```
chart_name_col <- dataset %>%
ggplot(aes(x = x_axis_variable, y = y_axis_variable, fill = clustered_variable)) + # in example clustered_variables are ACT and SAT
  geom_bar(position = "dodge", stat = "identity") +
  scale_fill_manual(values = c("#color_code", "#color_code"), labels = c("clustered_value1", "clustered_value2")) +  # to manual label clustered values black + white
  labs(x =  "x_axis_title", y = "y_axis_title", fill = "clustered_variable", title = "title of chart, only capitalize first word") +
  scale_y_continuous(breaks = c(0.2, 0.4, 0.6), 
                    labels = c("20%", "40%", "60%")) + # decide how to scale y axis
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1),
        text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        plot.title = element_text(size = 16)) +
theme(panel.grid.major = element_blank(),
        panel.grid.minor = element_blank())
```
</details>

## Basic Scatter Plot

```
chart_name_col <- dataset %>%
  ggplot(aes(x = x_axis_variable, y = y_axis_variable)) + 
  geom_point(color = "point_color", size = 3) + # Adds the dots and choose color
  heme_minimal()+
  theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)))+
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```

## Scatter Plot with labels

```
chart_name_col <- dataset %>%
  ggplot(aes(x = x_axis_variable, y = y_axis_variable, col = dot_color_variable, label = dot_label_variable))+
  geom_point(size = 3, # can adjust dot size as needed
             show.legend = FALSE) + # hide legend
  geom_text_repel(data = subset(dataset, test == 1), 
                  family = "Palatino",
                  size = 4.3,
                  color = "black",
                  nudge_y = 3000,
                  segment.color = NA,
                  show.legend = FALSE) +
  geom_text_repel(data = subset(dataset, test == 0), 
                  family = "Palatino",
                  size = 3.1,
                  color = "black",
                  nudge_y = 2500,
                  direction = "x",
                  segment.color = NA,
                  show.legend = FALSE) +
  scale_color_manual(values = cols) +
  theme_minimal()+
  theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)))+
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```

## Pie Chart

## Tree Plot

```
tree_data %>%
ggplot(aes(area = count, fill = school, label = school_clean)) +
geom_treemap(colour = "white", size = 4) +
scale_fill_manual(values = cols_trees, name = "School") +
geom_treemap_text(aes(label = percent, family = "Palatino", place = "topleft", size = 20, reflow = TRUE, padding.x = grid::unit(3, "mm"), padding.y = unit(13, "mm")) +
theme_minimal() +
labs(title = "Percent of TSL Staff from Each College") +
theme(legend.position = "none",
text = element_text(family = "Palatino"),
plot.title = element_text(size = 20))
```

## Line Plot


# Saving and Exporting

