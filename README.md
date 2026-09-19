
# Set Up

# Specific Charts

## Bar Chart

### Simple Horizontal Bar Chart

```
color_viz <- policy %>%
  ggplot(aes(x = reorder(Policy, order), y = Count, fill = Policy)) +
  geom_col() +
#  geom_text(aes(label = Count), vjust = -0.5) +
  scale_x_discrete(labels = function(x) str_wrap(x, width = 20)) +
  scale_fill_manual(values = cols, name = "Cylinders") +
  theme_minimal() +
  theme(legend.position = "none",
        axis.title.x = element_text(margin = margin(t = 15)),
        axis.title.y = element_text(margin = margin(r = 10)),
        text = element_text(family = "Palatino")) +
  labs(x = "Institution Policy", y = "Number of Universities", title = "Institution-Wide AI Policy at Top 100 U.S. Universities")

color_viz
```
<details>
  <summary><b>Click here to expand</b></summary>
<details>

## Scatter Plot

## Pie Chart

## Tree Plot

## Line Plot


# Saving and Exporting

