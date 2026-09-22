
# Set Up

## Color Palettes


<details>
  <summary><b>5C Colors</b></summary>

  ```
cols <- c("Pomona"= "#20438F", "Pitzer" = "#f68712", "Claremont McKenna" = "#980113", "Scripps" = "#33715a", "Harvey Mudd" = "#edaa00",
                   "POM" = "#20438F", "PIT" = "#f68712", "CMC" = "#980113", "SCR" = "#33715a", "HMC" = "#edaa00")
```
  
</details>

<details>
  <summary><b>5C Black and White</b></summary>

```
bw <- c("Pomona"= "#3F3F46", "Pitzer" = "#71717B", "Claremont McKenna" = "#D4D4D8", "Scripps" = "#000000", "Harvey Mudd" = "#9F9FA9",
                  "POM" = "#3F3F46", "PIT" = "#71717B", "CMC" = "#D4D4D8", "SCR" = "#000000", "HMC" = "#9F9FA9")
```
  
</details>

</details>

#### Generate Color Palettes [here](https://r-graph-gallery.com/color-palette-finder)

# Specific Charts


## Column Chart
<img width="480" height="360" alt="ai-professor-policy-color" src="https://github.com/user-attachments/assets/fd3f3033-ad33-4215-b7b7-cafa49fed8fa" />
<details>
  <summary><b>Color version</b></summary>
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
</details>

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

## Stacked Bar Chart
<img width="300" height="180" alt="tsl_race" src="https://github.com/user-attachments/assets/e585d100-3dc0-420e-a80a-ebe400c0844a" />

<details>
  <summary><b>Color version</b></summary>
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
</details>

  
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

## Horizontal Bart Chart


## Clustered Bar Chart
<img width="300" height="180" alt="cmc_test" src="https://github.com/user-attachments/assets/e7904928-f2e4-49e8-b15f-48210e464de1" />

<details>
  <summary><b>Color version</b></summary>
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
</details>

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
<img width="386" height="225" alt="image" src="https://github.com/user-attachments/assets/9fc896bc-5dab-4c93-80b0-1fa0e917a9ff" />

<details>
  <summary><b>Can use same for black/white and color</b></summary>

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
</details>

## Scatter Plot with labels
<img width="768" height="576" alt="image" src="https://github.com/user-attachments/assets/b141daa2-3c49-4a5d-b990-588b4ffa66a6" />

<details>
  <summary><b>Color version</b></summary>
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
</details>
  
<details>
  <summary><b>Black and white version</b></summary>
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
  scale_color_manual(values = bw) +
  theme_minimal()+
  theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)))+
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```
</details>
  
## Pie Chart

<img width="334" height="240" alt="pie_example" src="https://github.com/user-attachments/assets/6a6e9c20-ae1a-450d-9097-f09e2e8ba83a" />


<details>
  <summary><b>Color version</b></summary>

```
dataframe %>%
  ggplot(aes(x="", y = percentage_variable, fill=reorder(x_variable, count))) +
  geom_bar(stat="identity", width=4, color = "white") +
  coord_polar("y", start=0) +
  theme_void() +
  scale_fill_manual(name = "", values = x_variable_color) +
  geom_text(data = subset(data_gen, percent >= 10), # only makes labels for percentages greater than 10%
      aes(label = paste0(percent, "%")), # adds a % sign after the number, not always necessary
      position = position_stack(vjust = 0.6), # adjust to 'float' labels into proper position
      family = "Palatino", size = 5, color = "black") +
  labs(title = "title") +
  theme(text = element_text(family = "Palatino", size = 12), plot.title = element_text(vjust = -2))

```

</details>

<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  dataframe %>%
    ggplot(aes(x="", y = percentage_variable, fill=reorder(x_variable, count))) +
    geom_bar(stat="identity", width=4, color = "white") +
    coord_polar("y", start=0) +
    theme_void() +
    geom_text(data = subset(data_gen, percent >= 10), # only makes labels for percentages greater than 10%
        aes(label = paste0(percent, "%")), # adds a % sign after the number, not always necessary
        position = position_stack(vjust = 0.6), # adjust to 'float' labels into proper position
        family = "Palatino", size = 5, color = "black") +
    labs(title = "title") +
    theme(text = element_text(family = "Palatino", size = 12), plot.title = element_text(vjust = -2)) +
    scale_fill_manual(name = "", values = x_variable_bw) #only difference from color version
  ```

</details>

## Tree Plot

<img width="627" height="267" alt="tree_example" src="https://github.com/user-attachments/assets/7697dd30-e56e-44ad-925c-3cd1aee81368" />


<details>
  <summary><b>Color version</b></summary>

  ```
dataframe %>%
  ggplot(aes(area = count, fill = color_variable, label = color_variable_name)) +
  geom_treemap(colour = "white", size = 4) +
  scale_fill_manual(values = cols_trees, name = "School") +
  geom_treemap_text(aes(label = percent, family = "Palatino", place = "topleft", size = 20, reflow = TRUE, padding.x = grid::unit(3, "mm"), padding.y = unit(13, "mm")) +
  theme_minimal() +
  labs(title = "title") +
  theme(legend.position = "none",
    text = element_text(family = "Palatino"),
    plot.title = element_text(size = 20))
```

  
</details>


<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  dataframe %>%
    ggplot(aes(area = count, fill = color_variable, label = color_variable_name)) +
    geom_treemap(colour = "white", size = 4) +
    scale_fill_manual(values = color_variable_bw, name = "School") + # difference from color version
    geom_treemap_text(aes(label = percent, family = "Palatino", place = "topleft", size = 20, reflow = TRUE, padding.x = grid::unit(3, "mm"), padding.y = unit(13, "mm")) +
    theme_minimal() +
    labs(title = "title") +
    theme(legend.position = "none",
      text = element_text(family = "Palatino"),
      plot.title = element_text(size = 20))
  ```

</details>

## Line Plot

<img width="629" height="395" alt="line_example" src="https://github.com/user-attachments/assets/5e4b166f-63b1-4fc6-8d4e-701d5ff9b4b0" />


Here, "line_one" and "line_two" refer to **Groceries** and **SNAP** respectively. The colors are coded directly using **scale_color_manual**.

<details>
  <summary><b>Color version</b></summary>

  ```
line_data %>%
  ggplot(aes(x = x_variable, y = y_variable)) +
  geom_line(aes(color = "line_one"), linewidth = 1.2) +
  geom_line(data = dataframe, aes(x = x_variable, y = y_variable, color = "line_two"), linewidth = 1.2) +
  scale_color_manual(values = c("line_one" = "#F03282", "line_two" = "#156FB0"), name = "") +
  scale_y_continuous(limits = c(250, 1100),
                     breaks = c(400, 600, 800, 1000)) + # custom ticks for y axis
  labs(title = "title", x = "x axis title", y = "y axis title") +
  theme_minimal() +
  theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)))
```

  
</details>


<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  dataframe %>%
    ggplot(aes(x = x_variable, y = y_variable)) +
    geom_line(aes(color = "line_one"), linewidth = 1.2) +
    geom_line(data = dataframe, aes(x = x_variable, y = y_variable, color = "line_two"), linewidth = 1.2) +
    scale_color_manual(values = c("line_one" = "#91919C", "line_two" = "#222225") +
    scale_y_continuous(limits = c(250, 1100),
                     breaks = c(400, 600, 800, 1000)) + # custom ticks for y axis
    labs(title = "title", x = "x axis title", y = "y axis title") +
    theme_minimal() +
    theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank())
  ```

</details>

# Saving and Exporting

