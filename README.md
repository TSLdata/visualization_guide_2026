
# Set Up

# Specific Charts

## Bar Chart

### Simple Horizontal Bar Chart

```
chart_name <- data %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
  scale_fill_manual(values = cols, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        text = element_text(family = "Palatino")) +
  labs(x = "x_axis_title", y = "y_axis_title", title = "title of chart, only capitalize first word")
```
<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  b_w_axis <- policy %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
#  geom_text(aes(label = Count), vjust = -0.5) +
  scale_x_discrete(labels = function(x) str_wrap(x, width = 20)) +
  scale_fill_manual(values = b_w, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank(),
        axis.line.x = element_line(colour = "black", linewidth = 0.2),
        axis.line.y = element_line(colour = "black", linewidth = 0.2),
        text = element_text(family = "Palatino")) +
  labs(x = "Institution Policy", y = "Number of Universities", title = "Institution-Wide AI Policy at Top 100 U.S. Universities")
    
  ```

</details>

## Scatter Plot

## Pie Chart

<img width="546" height="400" alt="pie_example" src="https://github.com/user-attachments/assets/fcea62ff-eca3-4ff6-b2cd-65e2e191bd2e" />


<details>
  <summary><b>Color version</b></summary>

```
pie_data %>%
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
  pie_data %>%
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

<img width="550" height="220" alt="tree_example" src="https://github.com/user-attachments/assets/91dcf0d5-d702-452d-9e7e-d2ca8214d326" />


<details>
  <summary><b>Color version</b></summary>

  ```
tree_data %>%
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
  tree_data %>%
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

<img width="626" height="382" alt="line_example" src="https://github.com/user-attachments/assets/0b6f9244-cded-4a57-8bba-c85cdd525ca7" />


<details>
  <summary><b>Color version</b></summary>

  ```
line_data %>%
  ggplot(aes(x = x_variable, y = y_variable)) +
  geom_line(aes(color = "line_one"), linewidth = 1.2) +
  geom_line(data = snap_clean, aes(x = date, y = cost, color = "line_two"), linewidth = 1.2) +
  scale_color_manual(values = c("line_one" = "#F03282", "line_two" = "#156FB0"), name = "") +
  scale_y_continuous(limits = c(250, 1100),
                     breaks = c(400, 600, 800, 1000)) + # custom ticks for y axis
  labs(title = "title", x = "x_axis_title", y = "y_axis_title") +
  theme_minimal() +
  theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)))
```

  
</details>


<details>
  <summary><b>Black and white version</b></summary>
  
  ```
  line_data %>%
    ggplot(aes(x = x_variable, y = y_variable)) +
    geom_line(aes(color = "line_one"), linewidth = 1.2) +
    geom_line(data = snap_clean, aes(x = date, y = cost, color = "line_two"), linewidth = 1.2) +
    scale_color_manual(values = c("line_one" = "#91919C", "line_two" = "#222225") +
    scale_y_continuous(limits = c(250, 1100),
                     breaks = c(400, 600, 800, 1000)) + # custom ticks for y axis
    labs(title = "title", x = "x_axis_title", y = "y_axis_title") +
    theme_minimal() +
    theme(text = element_text(family = "Palatino"),
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank())
  ```

</details>

# Saving and Exporting

